<template>
	<view class="content">
		<view class="title-text">
			{{title}}
		</view>
		<view class="video">
			<video class="video-box" src="https://www.eme.cn/attachment/online_course/video/20210114/1610592080u9uja.mp4"
			 @waiting="loading" @timeupdate="timeupdate" :danmu-list="danmuList" enable-danmu danmu-btn controls>

			</video>
			<!-- 			<video class="video-box" src="@/static/1610591345o6dt0.mp4">
				
			</video> -->
			<view class="danmu">

				<view class="danmu-form">
					<view class="label">弹幕内容</view>
					<view class="">
						<input v-model="danmuValue" class="uni-input" type="text" placeholder="在此处输入弹幕内容" />
					</view>
				</view>
				<view class="uni-btn-v">
					<button @click="sendDanmu" type="primary" class="page-body-button">发送弹幕</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '视频、弹幕',
				danmuList: [{
						text: '第 1s 出现的弹幕',
						color: '#ff0000',
						time: 1
					},
					{
						text: '第 1.4s 出现的弹幕',
						color: '#ff0000',
						time: 1.4
					},
					{
						text: '第 1s 出现的弹幕',
						color: '#ff0000',
						time: 2.1
					},
					{
						text: '第 1s 出现的弹幕',
						color: '#ff0000',
						time: 2.5
					},
					{
						text: '第 3s 出现的弹幕',
						color: '#ff00ff',
						time: 3
					}
				],
				danmuValue: ''
			};
		},
		components: {},
		onReady() {
			// #ifndef MP-ALIPAY
			this.videoContext = uni.createVideoContext('myVideo')
			// #endif
		},
		onLoad() {

		},
		methods: {
			loading(e) {
				// console.log(e)
				uni.showLoading({
					title: '我很努力工作...'
				})
			},
			timeupdate(e) {
				// console.log(e)
				uni.hideLoading()
			},
			sendDanmu() {
				console.log(this.danmuValue);
				this.videoContext.sendDanmu({
					text: this.danmuValue,
					color: this.getRandomColor(),
				});
				this.danmuValue = '';
			},
			videoErrorCallback: function(e) {
				uni.showModal({
					content: e.target.errMsg,
					showCancel: false
				})
			},
			getRandomColor: function() {
				const rgb = []
				for (let i = 0; i < 3; ++i) {
					let color = Math.floor(Math.random() * 256).toString(16)
					color = color.length == 1 ? '0' + color : color
					rgb.push(color)
				}
				return '#' + rgb.join('')
			}
		}
	};
</script>

<style lang="scss">
	.content {
		text-align: center;

		.title-text {
			font-size: 32rpx;
			margin: 30rpx 0;
		}

		.video-box {
			width: 100%;
			height: 430rpx;
		}
		.danmu {
			margin: 30rpx;
			.danmu-form {
				display: flex;
				margin-bottom: 30rpx;
			}	
		}
		
	}
</style>
