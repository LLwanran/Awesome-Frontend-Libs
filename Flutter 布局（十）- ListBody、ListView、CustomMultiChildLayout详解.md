# Flutter 布局（十）- ListBody、ListView、CustomMultiChildLayout详解

> 本文主要介绍Flutter布局中的ListBody、ListView、CustomMultiChildLayout控件，详细介绍了其布局行为以及使用场景，并对源码进行了分析。

## 1. ListBody

> A widget that arranges its children sequentially along a given axis.

### 1.1 简介

ListBody是一个不常直接使用的控件，一般都会配合ListView或者Column等控件使用。ListBody的作用是按给定的轴方向，按照顺序排列子节点。

### 1.2 布局行为

在主轴上，子节点按照顺序进行布局，在交叉轴上，子节点尺寸会被拉伸，以适应交叉轴的区域。

在主轴上，给予子节点的空间必须是不受限制的（unlimited），使得子节点可以全部被容纳，ListBody不会去裁剪或者缩放其子节点。

### 1.3 继承关系

~~~
Object > Diagnosticable > DiagnosticableTree > Widget > RenderObjectWidget > MultiChildRenderObjectWidget > ListBody
~~~

### 1.4 示例代码

~~~
Flex(
  direction: Axis.vertical,
  children: <Widget>[
    ListBody(
      mainAxis: Axis.vertical,
      reverse: false,
      children: <Widget>[
        Container(color: Colors.red, width: 50.0, height: 50.0,),
        Container(color: Colors.yellow, width: 50.0, height: 50.0,),
        Container(color: Colors.green, width: 50.0, height: 50.0,),
        Container(color: Colors.blue, width: 50.0, height: 50.0,),
        Container(color: Colors.black, width: 50.0, height: 50.0,),
      ],
  )],
)
~~~

### 1.5 源码解析

构造函数如下：

~~~
ListBody({
  Key key,
  this.mainAxis = Axis.vertical,
  this.reverse = false,
  List<Widget> children = const <Widget>[],
})
~~~

#### 1.5.1 属性解析

**mainAxis**：排列的主轴方向。

**reverse**：是否反向。

#### 1.5.2 源码

ListBody的布局代码非常简单，根据主轴的方向，对子节点依次排布。

当向右的时候，布局代码如下，向下的代码类似：

~~~
double mainAxisExtent = 0.0;
RenderBox child = firstChild;
switch (axisDirection) {
case AxisDirection.right:
  final BoxConstraints innerConstraints = new BoxConstraints.tightFor(height: constraints.maxHeight);
  while (child != null) {
    child.layout(innerConstraints, parentUsesSize: true);
    final ListBodyParentData childParentData = child.parentData;
    childParentData.offset = new Offset(mainAxisExtent, 0.0);
    mainAxisExtent += child.size.width;
    assert(child.parentData == childParentData);
    child = childParentData.nextSibling;
  }
  size = constraints.constrain(new Size(mainAxisExtent, constraints.maxHeight));
  break;
}
~~~

当向左的时候，布局代码如下，向上的代码类似：

~~~
double mainAxisExtent = 0.0;
RenderBox child = firstChild;
case AxisDirection.left:
  final BoxConstraints innerConstraints = new BoxConstraints.tightFor(height: constraints.maxHeight);
  while (child != null) {
    child.layout(innerConstraints, parentUsesSize: true);
    final ListBodyParentData childParentData = child.parentData;
    mainAxisExtent += child.size.width;
    assert(child.parentData == childParentData);
    child = childParentData.nextSibling;
  }
  double position = 0.0;
  child = firstChild;
  while (child != null) {
    final ListBodyParentData childParentData = child.parentData;
    position += child.size.width;
    childParentData.offset = new Offset(mainAxisExtent - position, 0.0);
    assert(child.parentData == childParentData);
    child = childParentData.nextSibling;
  }
  size = constraints.constrain(new Size(mainAxisExtent, constraints.maxHeight));
  break;
~~~

向右或者向下的时候，布局代码很简单，依次去排列。当向左或者向上的时候，首先会去计算主轴所占的空间，然后再去计算每个节点的位置。

### 1.6 使用场景

笔者自己从未使用过这个控件，也想象不出场景，大家了解下有这么一个布局控件即可。

## 2. ListView

> A scrollable, linear list of widgets.

### 2.1 简介

ListView是一个非常常用的控件，涉及到数据列表展示的，一般情况下都会选用该控件。ListView跟GridView相似，基本上是一个slivers里面只包含一个SliverList的CustomScrollView。

### 2.2 布局行为

ListView在主轴方向可以滚动，在交叉轴方向，则是填满ListView。

### 2.3 继承关系

~~~
Object > Diagnosticable > DiagnosticableTree > Widget > StatelessWidget > ScrollView > BoxScrollView > ListView
~~~

看继承关系可知，这是一个组合控件。ListView跟GridView类似，都是继承自BoxScrollView。

### 2.4 示例代码

~~~
ListView(
  shrinkWrap: true,
  padding: EdgeInsets.all(20.0),
  children: <Widget>[
    Text('I\'m dedicating every day to you'),
    Text('Domestic life was never quite my style'),
    Text('When you smile, you knock me out, I fall apart'),
    Text('And I thought I was so smart'),
  ],
)

ListView.builder(
  itemCount: 1000,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text("$index"),
    );
  },
)
~~~

两个示例都是官方文档上的例子，第一个展示四行文字，第二个展示1000个item。

### 2.5 源码解析

构造函数如下：

~~~
ListView({
  Key key,
  Axis scrollDirection = Axis.vertical,
  bool reverse = false,
  ScrollController controller,
  bool primary,
  ScrollPhysics physics,
  bool shrinkWrap = false,
  EdgeInsetsGeometry padding,
  this.itemExtent,
  bool addAutomaticKeepAlives = true,
  bool addRepaintBoundaries = true,
  double cacheExtent,
  List<Widget> children = const <Widget>[],
})
~~~

同时也提供了如下额外的三种构造方法，方便开发者使用。

~~~
ListView.builder
ListView.separated
ListView.custom
~~~

#### 2.5.1 属性解析

ListView大部分属性同GridView，想了解的读者可以看一下之前所写的GridView相关的文章。这里只介绍一个属性

**itemExtent**：ListView在滚动方向上每个item所占的高度值。

#### 2.5.2 源码

~~~
@override
Widget buildChildLayout(BuildContext context) {
  if (itemExtent != null) {
    return new SliverFixedExtentList(
      delegate: childrenDelegate,
      itemExtent: itemExtent,
    );
  }
  return new SliverList(delegate: childrenDelegate);
}
~~~

ListView标准构造布局代码如上所示，底层是用到的SliverList去实现的。ListView是一个slivers里面只包含一个SliverList的CustomScrollView。源码这块儿可以参考GridView，在此不做更多的说明。

### 2.6 使用场景

ListView使用场景太多了，一般涉及到列表展示的，一般都会选择ListView。

但是需要注意一点，ListView的标准构造函数适用于数目比较少的场景，如果`数目比较多`的话，最好使用`ListView.builder`。

ListView的标准构造函数会将所有item一次性创建，而ListView.builder会创建滚动到屏幕上显示的item。

## 3. CustomMultiChildLayout

> A widget that uses a delegate to size and position multiple children.

### 3.1 简介

之前单节点布局控件中介绍过一个类似的控件--CustomSingleChildLayout，都是通过delegate去实现自定义布局，只不过这次是多节点的自定义布局的控件，通过提供的delegate，可以实现控制节点的位置以及尺寸。

### 3.2 布局行为

CustomMultiChildLayout提供的delegate可以控制子节点的布局，具体在如下几点：

*   可以决定每个子节点的布局约束条件；
*   可以决定每个子节点的位置；
*   可以决定自身的尺寸，但是自身的自身必须不能依赖子节点的尺寸。

可以看到，跟CustomSingleChildLayout的delegate提供的作用类似，只不过CustomMultiChildLayout的稍微会复杂点。

### 3.3 继承关系

~~~
Object > Diagnosticable > DiagnosticableTree > Widget > RenderObjectWidget > MultiChildRenderObjectWidget > CustomMultiChildLayout
~~~

### 3.4 示例代码

~~~
class TestLayoutDelegate extends MultiChildLayoutDelegate {
  TestLayoutDelegate();

  static const String title = 'title';
  static const String description = 'description';

  @override
  void performLayout(Size size) {
    final BoxConstraints constraints =
        new BoxConstraints(maxWidth: size.width);

    final Size titleSize = layoutChild(title, constraints);
    positionChild(title, new Offset(0.0, 0.0));

    final double descriptionY = titleSize.height;
    layoutChild(description, constraints);
    positionChild(description, new Offset(0.0, descriptionY));
  }

  @override
  bool shouldRelayout(TestLayoutDelegate oldDelegate) => false;
}

Container(
  width: 200.0,
  height: 100.0,
  color: Colors.yellow,
  child: CustomMultiChildLayout(
    delegate: TestLayoutDelegate(),
    children: <Widget>[
      LayoutId(
        id: TestLayoutDelegate.title,
        child: new Text("This is title",
            style: TextStyle(fontSize: 20.0, color: Colors.black)),
      ),
      LayoutId(
        id: TestLayoutDelegate.description,
        child: new Text("This is description",
            style: TextStyle(fontSize: 14.0, color: Colors.red)),
      ),
    ],
  ),
)
~~~

上面的TestLayoutDelegate作用很简单，对子节点进行尺寸以及位置调整。可以看到，`每一个子节点必须用一个LayoutId控件包裹起来`，在delegate中可以对不同id的控件进行调整。

### 3.5 源码解析

构造函数如下：

~~~
CustomMultiChildLayout({
  Key key,
  @required this.delegate,
  List<Widget> children = const <Widget>[],
})
~~~

#### 3.5.1 属性解析

**delegate**：对子节点进行尺寸以及位置调整的delegate。

#### 3.5.2 源码

~~~
@override
void performLayout() {
  size = _getSize(constraints);
  delegate._callPerformLayout(size, firstChild);
}
~~~

CustomMultiChildLayout的布局代码很简单，调用delegate中的布局函数进行相关的操作，本身做的处理很少，在这里不做过多的解释。

### 3.6 使用场景

一些比较复杂的布局场景可以使用，但是有很多可替代的控件，使用起来也没有这么麻烦，大家还是按照自己熟练程度选择使用。

## 4. 参考

1.  [ListBody class](https://docs.flutter.io/flutter/widgets/ListBody-class.html)
2.  [ListView class](https://docs.flutter.io/flutter/widgets/ListView-class.html)
3.  [CustomMultiChildLayout class](https://docs.flutter.io/flutter/widgets/CustomMultiChildLayout-class.html)
4.  [Working with long lists](https://flutter.io/cookbook/lists/long-lists/)
