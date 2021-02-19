<template>
	<view class="content">
		<template v-for=" (list, index) in lists" v-if="lists">
			<navigator :url="list.link" open-type="navigate" :key="index">
				<view class="list">
					<view class="img">
						<view class="icon" :class="list.icon"></view>
					</view>
					<view class="content">
						<view class="title">
							{{list.title}}
						</view>
						<view class="desc">
							{{list.desc}}
						</view>
					</view>
				</view>
			</navigator>

		</template>
	</view>
</template>

<script>
	import apiData from "@/apis/component.js"
	export default {
		data() {
			return {
				title: '',
				lists : ''
			}
		},
		onLoad() {
			this.lists = apiData.lists;
			this.title = apiData.title;
			console.log('apiData',apiData.title, typeof this.lists)
		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
.content {
	.list {
		width: 100%;
		display: flex;
		padding: 30rpx;
		border-bottom: 1rpx solid #dedede;
		.img {
			margin-right: 30rpx;
			display: flex;
			align-items: center;
			.icon {
				font-size: 70rpx;
				&.lIcon-chart-1 {
					font-size: 80rpx;
				}
			}
		}
		.title {
			font-size: 28rpx;
		}
		.desc {
			color: #999;
			font-size: 24rpx;
		}
	}
}
</style>
