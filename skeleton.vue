<template>
	<view>
		<view class="skeleton" v-show="loading" :class="[animationClass]" v-for="skeleton in count">
			<view class="row" >
				<view v-for="(item,index) in row" :key="item">
					<view :style="{width:rowWidth,height:rowHeight}" v-if="variant === 'image'" :class="[varianttype]">
						<svg  viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg">
						    <path d="M64 896V128h896v768H64z m64-128l192-192 116.352 116.352L640 448l256 307.2V192H128v576z m224-480a96 96 0 1 1-0.064 192.064A96 96 0 0 1 352 288z"/>
						</svg>
					</view>
					<view v-else :class="[varianttype]" :style="{width:rowWidth,height:rowHeight}"  class="row-class"></view>
				</view>
			</view>
		</view>
		<slot v-if="!loading"></slot>
	</view>
</template>
<script>
	export default {
		props: {
			//是否使用动画
			animate: {
				type: Boolean,
				default: false
			},
			//渲染多少个 template, 建议使用尽可能小的数字
			count: {
				type: Number,
				default: 1
			},
			//是否显示 skeleton 骨架屏
			loading: {
				type: Boolean,
				default: true
			},
			//骨架屏段落数量
			row: {
				type: Number,
				default: 1
			},
			//段落行宽度，默认为100%
			rowWidth:{
				type: String | Number,
				default: '100%'
			},
			//段落行高度
			rowHeight:{
				type: String | Number
			},
			//当前显示的占位元素的样式
			variant: {
				type: String,
				values: [
				      'circle',
				      'h1',
				      'h3',
				      'text',
				      'caption',
				      'p',
				      'image',
				      'button',
				],
				default: 'text'
			}
		},
		computed: {
			animationClass() {
				return [this.animate ? 'skeleton_animation' : '']
			},
			varianttype(){
				return [this.variant ? 'skeleton__'+this.variant : 'text']
			}
		},
		data() {
			return {
			}
		}
	}
</script>

<style lang="scss" scoped>
	/* 占位元素的样式 */
	$skeleton-h1-height: 20px;
	$skeleton-h3-height: 18px;
	$skeleton-caption-height: 12px;
	$skeleton-button-height:40px;
	$skeleton-button-width:64px;
	$skeleton-circle-width:36px;
	$skeleton-circle-height:36px;
	$skeleton-text-height:13px;
	$skeleton-p-height:13px;
	$skeleton-image-width:200px;
	$skeleton-image-height:200px;
	$skeleton-image-svg-width:22%;
	$skeleton-image-svg-height:22%;
	
	.skeleton {
		background-color: #fff;
	}
	
	.row-class {
		width: 100%;
		height: 16px;
		margin-top: 12px;
	}
	
	.skeleton_animation .row-class,.skeleton__image {
		background: linear-gradient(
		90deg,#f2f2f2 25%,#e6e6e6 37%,#f2f2f2 63%);
		background-size: 400% 100%;
		animation: skeleton-loading 1.4s ease infinite;
	}

	@keyframes skeleton-loading{
		0%{
			background-position:100% 50%
		}
		to{
			background-position:0 50%
		}
	}
	.skeleton__h1 {
		height: $skeleton-h1-height;
	}
	.skeleton__h3 {
		height: $skeleton-h3-height;
	}
	.skeleton__caption {
	    height: $skeleton-caption-height;
	}
	.skeleton__button {
	    height: $skeleton-button-height;
		width: $skeleton-button-width;
		border-radius: 4px;
	}
	.skeleton__circle {
	    height: $skeleton-circle-height;
		width: $skeleton-circle-width;
		border-radius: 50%;
		line-height: $skeleton-circle-height;
	}
	.skeleton__text {
	    width: 100%;
	    height:  $skeleton-text-height;
	}
	.skeleton__p {
	    width: 100%;
	    height: $skeleton-p-height;
	}
	.skeleton__image {
		width: $skeleton-image-width;
		height:$skeleton-image-height;
		background-color: #f2f2f2;
	    display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 0;
	}
	.skeleton__image svg {
	    fill: #dcdde0;
	    width: $skeleton-image-svg-width;
	    height: $skeleton-image-svg-height;
	}
</style>
