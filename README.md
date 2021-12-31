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
| variant | String |text| 当前显示的占位元素的样式，可选值 p / text / h1 / h3 / caption / button / image / circle |

## 示例代码

```html
<template>
	<view>
		<view class="content">
			<p>基础用法(列表):</p>
			
			<skeleton :row='3' :animate='true' :loading='loading' variant='p'>
				<view >
				 <p>测试新闻标题1号</p>
				 <p>测试新闻标题2号</p>
				 <p>测试新闻标题3号</p>
				</view>
			</skeleton>
			 <p>图片+标题:</p>
				<skeleton :animate='true' :loading='loading' variant='image'>
					<view >
						<image src='https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1686&q=800'></image>
					</view>
				</skeleton>
				<skeleton :animate='true' :loading='loading' variant='h1'>
					<view >
						<h1>萌猫大作战1.0</h1>
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
</style>
```

## 效果图

![图片描述](https://doc.shiyanlou.com/courses/5791/1693782/22dce59e4041c08bc3b44d7862a93c3c-0)

