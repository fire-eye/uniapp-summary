<template>
	<view class="home">
		<view class="bg-grey padding-sm">
			<text>
				Uni-app项目开发中组件汇总
				前端开发知识汇总
			</text>
		</view>
		<view class="title padding-sm text text-bold bg-gradual-blue">
			{{title}} 
		</view>

		<view class="lists">
			<template v-for="( item, index ) in apiData.lists">
				<navigator :url="item.link" open-type="navigate" :key="index">
					<view class="list flex padding" :key="index">
						<view class="list-index text-xxxl text-white bg-gradual-blue radius text-bold flex justify-center align-center margin-right-sm">
							{{index}}
						</view>
						<view class="list-content flex-sub">
							<view class="title text-bold">
								{{item.title}}
							</view>
							<view class="desc text-sm text-gray">
								{{item.desc}}
							</view>
						</view>
						<view class="lIcon-arrow-right flex justify-center align-center text-xxl">
							
						</view>
					</view>
				</navigator>
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
			apiData ,
			
		};
	},
	components: {
	},
	onLoad() {
		let t=this;
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

<style lang="scss" scoped>
.home {
	
	.lists {
		background-color: #fff;
		.list {
			border-bottom: 1rpx solid #dedede;
			line-height: 40rpx;
			.list-index {
				width: 120rpx;
				height: 120rpx;
			}
		}
		.img {
			
		}
	}
}
</style>
