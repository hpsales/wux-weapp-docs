# SwipeAction 滑动操作

用于滑动操作组件。

## 使用指南

### 在 page.json 中引入组件

```json
{
    "navigationBarTitleText": "SwipeAction",
    "usingComponents": {
        "wux-swipe-action-group": "../../dist/swipe-action-group/index",
        "wux-swipe-action": "../../dist/swipe-action/index",
        "wux-cell-group": "../../dist/cell-group/index",
        "wux-cell": "../../dist/cell/index",
        "wux-icon": "../../dist/icon/index"
    }
}
```

### 示例

```html
<view class="page">
    <view class="page__hd">
        <view class="page__title">SwipeAction</view>
        <view class="page__desc">滑动操作</view>
    </view>
    <view class="page__bd">
        <view class="sub-title">With swipeActionGroup</view>
        <wux-swipe-action-group>
            <wux-swipe-action autoClose left="{{ left }}" right="{{ right }}" bind:click="onClick">
                <view class="demo-item">Have left and right buttons</view>
            </wux-swipe-action>
            <wux-swipe-action autoClose left="{{ left }}">
                <view class="demo-item">Only left buttons</view>
            </wux-swipe-action>
            <wux-swipe-action autoClose right="{{ right }}">
                <view class="demo-item">Only right buttons</view>
            </wux-swipe-action>
            <wux-swipe-action autoClose useSlots>
                <view slot="left">
                    <view class="demo-button"><wux-icon type="ios-heart" /></view>
                </view>
                <view slot="right">
                    <view class="demo-button" bindtap="onShare"><wux-icon type="ios-share-alt" /></view>
                </view>
                <view class="demo-item">UseSlots</view>
            </wux-swipe-action>
        </wux-swipe-action-group>
        <view class="sub-title">With cellGroup</view>
        <wux-cell-group>
            <wux-swipe-action autoClose left="{{ left }}" right="{{ right }}" bind:click="onClick">
                <wux-cell title="Have left and right buttons"></wux-cell>
            </wux-swipe-action>
            <wux-swipe-action autoClose left="{{ left }}">
                <wux-cell title="Only left buttons"></wux-cell>
            </wux-swipe-action>
            <wux-swipe-action autoClose right="{{ right }}">
                <wux-cell title="Only right buttons"></wux-cell>
            </wux-swipe-action>
        </wux-cell-group>
    </view>
</view>
```

```js
Page({
    data: {
        right: [{
            text: 'Cancel',
            style: 'background-color: #ddd; color: white',
        },
        {
            text: 'Delete',
            style: 'background-color: #F4333C; color: white',
        }],
        left: [{
            text: 'Reply',
            style: 'background-color: #108ee9; color: white',
        },
        {
            text: 'Cancel',
            style: 'background-color: #ddd; color: white',
        }],
    },
    onClick(e) {
        console.log('onClick', e.detail)
    },
    onShare() {
        console.log('onShare')
    },
})
```

## 视频演示

[SwipeAction](./_media/swipe-action.mp4 ':include :type=iframe width=375px height=667px')

## API

### SwipeAction props

| 参数 | 类型 | 描述 | 默认值 |
| --- | --- | --- | --- |
| prefixCls | <code>string</code> | 自定义类名前缀 | wux-swipe |
| autoClose | <code>boolean</code> | 是否自动关闭 | false |
| disabled | <code>boolean</code> | 是否禁用 | false |
| left | <code>array</code> | 左侧按钮组，当 useSlots 为 false 时才生效 | [] |
| right | <code>array</code> | 右侧按钮组，当 useSlots 为 false 时才生效 | [] |
| useSlots | <code>boolean</code> | 是否使用插槽 | false |
| bind:click | <code>function</code> | 点击事件 | - |
| bind:open | <code>function</code> | 打开事件 | - |
| bind:close | <code>function</code> | 关闭事件 | - |

### SwipeAction slot

| 名称 | 描述 |
| --- | --- |
| - | 自定义内容 |
| left | 自定义左侧按钮组，当 useSlots 为 true 时才生效 |
| right | 自定义右侧按钮组，当 useSlots 为 true 时才生效 |