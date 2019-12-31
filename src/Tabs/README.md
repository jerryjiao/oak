# Tabs 标签页

## 使用

在页面`json`中引入组件：

```json
// import in `page.json`:
"usingComponents" : {
    "oak-tabs": "path/to/your/oakui/Tabs/tabs",
    "oak-tab": "path/to/your/oakui/Tab/tab"
}
```
在页面使用
```html
<!-- use in `page.wxml` -->
<oak-tabs bind:onChange="onChange">
    <oak-tab title="标签1">tab1</oak-tab>
    <oak-tab title="标签2">tab2</oak-tab>
    <oak-tab title="标签3">tab3</oak-tab>
</oak-tabs>
```
## 代码演示

### 基础用法
`tabs`的activeKey用来对应`tab`组件的索引值，默认是激活第一个标签， title是显示在标签栏上的名称
```
<oak-tabs activeKey="0" bind:onChange="onChange">
    <oak-tab title="标签1">tab1</oak-tab>
    <oak-tab title="标签2">tab2</oak-tab>
    <oak-tab title="标签3">tab3</oak-tab>
</oak-tabs>

Page({
    ononChange(e) {
        console.log(e.detail.key) //会返回当前激活的标签的索引值
    }
})
```

### 通过Key值匹配
如果`tab`组件传入了key值，`tabs`的activeKey用来对应激活标签的key值，默认是激活第一个标签，`tabs`的onChange事件会返回key的值
```
<oak-tabs activeKey="{{activeKey}}" bind:onChange="onChange">
    <oak-tab title="标签1" key="a">tab1</oak-tab>
    <oak-tab title="标签2" key="b">tab2</oak-tab>
    <oak-tab title="标签3" key="c">tab3</oak-tab>
</oak-tabs>

Page({
    data:{
        activeKey:0
    },
    ononChange(e) {
        console.log(e.detail.key)
    }
})
```

### 禁用标签
在`tab`组件上添加disabled可以禁用这个标签
```
<oak-tabs activeKey="0" bind:onChange="onChange">
    <oak-tab title="标签1">tab1</oak-tab>
    <oak-tab title="标签2" disabled>tab2</oak-tab>
    <oak-tab title="标签3">tab3</oak-tab>
</oak-tabs>
```

### 横向滚动
标签多于4个时，`tabs`可以横向滚动
```
<oak-tabs bind:onChange="onChange">
    <oak-tab title="标签1">tab1</oak-tab>
    <oak-tab title="标签2">tab2</oak-tab>
    <oak-tab title="标签3">tab3</oak-tab>
    <oak-tab title="标签4">tab4</oak-tab>
    <oak-tab title="标签5">tab5</oak-tab>
</oak-tabs>
```

### 样式风格
目前`tabs`支持两种样式风格: `normal`和`card`，默认为`normal`,可以通过`tabs`的`type`属性修改样式风格
```
<oak-tabs type="card">
    <oak-tab title="标签1">tab1</oak-tab>
    <oak-tab title="标签2">tab2</oak-tab>
    <oak-tab title="标签3">tab3</oak-tab>
</oak-tabs>

```
### 滑动切换
`tabs`上的添加`swipeable`属性可以开启滑动切换标签页

```
<oak-tabs swipeable>
    <oak-tab title="标签1">tab1</oak-tab>
    <oak-tab title="标签2">tab2</oak-tab>
    <oak-tab title="标签3">tab3</oak-tab>
</oak-tabs>
```

## API
API说明。
### Tabs Props
| 属性 | 说明 | 类型 | 默认值 |
|-----------|-----------|-----------|-------------|
| activeKey | 当前激活标签的值 | `String || Number` | 0 |
| color | 标签的颜色 | `String` | `#FD7622` | 
| z-inex | 设置`tabs`组件z-index的层级 | number | 1 | 
| type | 标签的样式类型，可选项为 `normal` 和 `card` | `String` |  `normal` |
| fixed | 是否固定在顶部 | Boolean | `false` |
| line-width | 底部条宽度(px) | `String || Number` | 与当前标签等宽 |
| line-height | 底部条高度(px) | `String || Number` | 3px |
| swipe-num | 开始滚动的的阈值，设置标签数量多少个可以滚动 | `Number` | 4 |
| swipeable | 是否开启滑动切换 | `Boolean` | `false` |
| onChange | 切换标签时触发 | `Function(key:String)` | - |


### Tabs Slot
| 名称 | 说明 | 
| --- | --- | --- |
| tabs-left | 标签栏左侧内容 |
| tabs-right | 标签栏右侧内容 | 

### Tab Props
| 属性 | 说明 | 类型 | 默认值 |
|-----------|-----------|-----------|-------------|
| key | 标签名称，作为匹配的标识符 | `string | number` | 标签的索引值 |
| title | 标题 | `string` | - |
| disabled | 是否禁用标签 | `boolean` | false | - |
| dot | 是否显示小红点 | `boolean` | - |
| info | 图标右上角提示信息 | `string | number` | - | 

### 外部样式类
| 类名 | 说明 | 
| --- | --- |
| ext-class | 根节点样式 | 
| tab-class | 标签样式类 | 
| tab-active-class | 标签激活状态样式类 |
