# skeleton 骨架屏

在需要等待加载内容的位置设置一个骨架屏，用法同 [elementui Skeleton 骨架屏](https://element.eleme.io/#/zh-CN/component/skeleton)类似。

## 属性说明

|属性名|类型|默认值|说明|
| -- | -- | --|--|
| animate | Boolean | false | 是否使用动画 |
| count | Number | 1 | 渲染多少个 template, 建议使用尽可能小的数字 |
| loading | Boolean | false | 是否显示 skeleton 骨架屏 |
| row | Number | 1 | 骨架屏段落数量 |
| rowWidth | String/Number | 100% | 段落行宽度，默认为100% |
| rowHeight | String/Number |  | 段落行高度，无默认值 |
| radius | String/Number |  | 圆角的边框，无默认值 |
| direction | String |column | 调整主轴方向，默认值为 column |
| mright | String/Number |  | 右侧外边距，无默认值 |
| variant | String |text| 当前显示的占位元素的样式，可选值 p / text / h1 / h3 / caption / button / image / circle |

## 示例代码

```html
<template>
	<view>
		<view class="content">
			<skeleton :row="4" direction='row' rowWidth="80px" radius='50%' rowHeight="80px" :animate='true' :loading='loading' variant='image'>
				<view class="imagelist-1">
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
				</view>
			</skeleton>
			<br/>
			<skeleton :row="4" direction='row'  rowWidth="80px" rowHeight="80px" :animate='true' :loading='loading' variant='image'>
				<view class="imagelist-2">
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
					<image src='https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1548&q=80'></image>
				</view>
			</skeleton>
			<br/>
			<skeleton :row='3' direction='column'  rowWidth="100%" rowHeight="13px" :animate='true' :loading='loading' variant='p'>
				<view >
				 <p>测试新闻标题1号</p>
				 <p>测试新闻标题2号</p>
				 <p>测试新闻标题3号</p>
				</view>
			</skeleton>
			<br/>
			<skeleton rowWidth="80px"  direction='row'  radius='50%' rowHeight="80px" :animate='true' :loading='loading' variant='image'>
				<view >
					<image src='https://images.unsplash.com/photo-1543852786-1cf6624b9987?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80'></image>
				</view>
			</skeleton>
			
			<skeleton  :animate='true' :loading='loading' variant='h1'>
				<view >
					<h1>标题</h1>
				</view>
			</skeleton>
			<skeleton :row='2' mright='8px' direction='row' :animate='true' :loading='loading' variant='text'>
				<view >
					<text>描述</text>
				</view>
			</skeleton>
			<skeleton :row='3' mright='8px' direction='row' :animate='true' :loading='loading' variant='text'>
				<view >
					<text>描述</text>
				</view>
			</skeleton>
			<skeleton :row='4' mright='8px' direction='row' :animate='true' :loading='loading' variant='text'>
				<view >
					<text>描述</text>
				</view>
			</skeleton>
	</view>
	</view>
</template>

<script>
	import skeleton from '../../components/lidao-skeleton/skeleton.vue'
	export default {
		data() {
			return {
				loading: true // 是否显示骨架屏组件
			}
		},
		onLoad() {
			// 通过延时模拟向后端请求数据，调隐藏骨架屏
			setTimeout(() => {
				this.loading = false;
			}, 3000)
		},components:{
			skeleton,
		}
	}
</script>
<style>
page{
	padding: 12px;
}
image{
	width: 80px;
	height: 80px;
	margin-right: 8px;
}
.imagelist-1 image{
	border-radius: 50%;
}
.imagelist-1 image:nth-last-child(1){
	margin-right: 0;
}
.imagelist-2 image:nth-last-child(1){
	margin-right: 0;
}
</style>

```

## 效果图

![图片描述](https://doc.shiyanlou.com/courses/7763/1693782/69bc26eb1c98c9e71476def878a517b1-0)