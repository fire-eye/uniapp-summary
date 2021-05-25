<template>
	<view class="content">
		<csh-item title="省市区联动选择器">
			name :  名称 <br/>
			code : 身份前缀代码
		</csh-item>
		<view class="flex align-center padding margin-sm bg-white">
			<view class="flex-sub">
				省市区
			</view>
			<view class="">
				<region :width="540" :isRevise="true" :previnceId="previnceId" :cityId="cityId" :countyId="countyId"
				@regionStr="regionStr" @region="region"></region>
			</view>
		</view>
	</view>
</template>

<script>
	import region from '@/components/region/region.vue'
	export default {
		components: { region },
		data() {
			return {
				previnceId : 35,
				cityId : 3502,
				countyId : 350206
				
			}
		},
		onLoad() {
			
		},
		methods: {
			regionStr(data){
				console.log(data)
			},
			region(data) {
				console.log(data)
			}
		}
	}
</script>

<style lang="scss" scoped>
.content {
	.list {
		width: 100%;
		display: flex;
		padding: 3.5%;
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
