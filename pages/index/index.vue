<template>
	<view class="content">
		页面 - 1
		<view class="title-text">
			{{title}}
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: 'Hello'
		};
	},
	onLoad() {},
	methods: {}
};
</script>

<style lang="scss">
.content {
	text-align: center;
	height: 400upx;
	margin-top: 200upx;
	.title-text {
		font-size: 32rpx;
	}
}
</style>
