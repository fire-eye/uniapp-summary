<template>
	<view class="content">
		页面 - 1
		<view class="title-text">
			{{title}}
		</view>
		<view class="video">
			<video class="video-box" src="https://www.eme.cn/attachment/online_course/video/20210114/1610592080u9uja.mp4" 
				@waiting="loading"
				@timeupdate="timeupdate"
				>
				
			</video>
<!-- 			<video class="video-box" src="@/static/1610591345o6dt0.mp4">
				
			</video> -->
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
	components: {
	},
	onLoad() {},
	methods: {
		loading(e){
			console.log(e)
			uni.showLoading({
				title:'我很努力工作...'
			})
		},
		timeupdate(e){
			console.log(e)
			uni.hideLoading()
		}
	}
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
	.video-box {
		width: 100%;
		height: 480rpx;
	}
}
</style>
