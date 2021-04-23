<template>
	<view class="home">
		<view class="bg-grey padding-sm">
			<text>
				Uni-app项目开发中常用组件汇总
				日常前端开发基础知识汇总
			</text>
		</view>
		<view class="title padding-sm text text-bold bg-gradual-blue">
			{{title}} 
		</view>

		<view class="lists">
			<template v-for="( item, index ) in 6">
				<view class="list flex padding" :key="index">
					<view class="img margin-right-sm">
						<image src="/static/img/video.png" mode=""></image>
					</view>
					<view class="list-content flex-sub">
						<view class="title">
							标题 - {{index}}
						</view>
						<view class="desc text-sm text-gray">
							内容介绍内容介绍内容介绍内容介绍内容介绍内容介绍内容介绍内容介绍内容介绍内容介绍内容
						</view>
					</view>
				</view>
			</template>
			
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: '最新更新',
			
		};
	},
	components: {
	},
	onLoad() {

	},
	methods: {
		loading(e){
			// console.log(e)
			uni.showLoading({
				title:'我很努力工作...'
			})
		},
		timeupdate(e){
			// console.log(e)
			uni.hideLoading()
		},
		
	}
};
</script>

<style lang="scss">
.home {
	
	.lists {
		background-color: #fff;
		.list {
			border-bottom: 1rpx solid #dedede;
			line-height: 46rpx;
		}
		.img {
			width: 140rpx;
			height: 140rpx;
			image {
				width: 100%;
				height: 100%;
			}
		}
	}
}
</style>
