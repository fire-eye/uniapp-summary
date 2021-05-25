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

		<view class="lists" v-if="lists">
			<template v-for="( item, index ) in lists">
				<view class="list flex padding-sm" :key="index">
					<view class="flex justify-center align-center img margin-right-sm bg-gradual-blue text-xxxl radius">
						{{index + 1}}
					</view>
					<view class="list-content flex-sub">
						<view class="title">
							{{item.title}}
						</view>
						<view class="desc text-sm text-gray">
							{{item.desc}}
						</view>
					</view>
				</view>
			</template>
			
		</view>
	</view>
</template>

<script>
	import apiData from "@/apis/component.js"
export default {
	data() {
		return {
			title: '最新更新',
			lists : ''
		};
	},
	components: {
	},
	onLoad() {
		this.lists = apiData.lists;
		console.log('apiData',apiData.title, apiData)
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
			line-height: 32rpx;
		}
		.img {
			width: 80rpx;
			height: 80rpx;
			image {
				width: 100%;
				height: 100%;
			}
		}
	}
}
</style>
