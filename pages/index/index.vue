<template>
	<view class="content">
		<custom-header :title="title" :backBtnClass="backBtnClass" :showBack="showBack" :containerStyle="containerStyle" :titleStyle="titleStyle" @backTap="backClick" ref="backTap"></custom-header>
		<view style="padding-bottom: 1500upx;">
			<view class="param-info">插件参数列表:</view>
			<view class="param-info">导航文字:title,变量类型:String</view>
			<view class="param-info">顶部导航容器样式字符串:containerStyle,变量类型:String</view>
			<view class="param-info">标题导航样式字符串:headerStyle,变量类型:String</view>
			<view class="param-info">左侧返回按钮样式类:backBtnClass,变量类型:String</view>
			<view class="param-info">标题样式字符串:titleStyle,变量类型:String</view>
			<view class="param-info">是否显示返回按钮:showBack,变量类型:Boolean</view>
			<view class="param-info">点击返回事件调用的方法:showBack</view>
		</view>
	</view>
</template>

<script>
	import customHeader from '@/components/custom-header.vue';
	export default {
		data() {
			return {
				title: '主页导航文字',
				showBack: true,
				backBtnClass: 'uni-icon uni-icon-back',
				containerStyle:'background:#ffffff',
				titleStyle: 'font-size:15px'
			}
		},
		components: {
			customHeader
		},
		onLoad() {

		},
		methods: {
			backClick() {
				uni.showToast({
					title: '调用自定义返回方法',
					icon: 'none'
				})
			}
		}
	}
</script>

<style>
	@import "../../common/uni.css";

	.param-info{
		text-align: left;
		padding-left: 50upx;
	}

</style>
