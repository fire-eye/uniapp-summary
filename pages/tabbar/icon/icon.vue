<template>
	<view class="content">
		<template v-for=" (item, index) in iconArr">
			<view class="tabbar-icon " :key="index">
				<view class="icon animated infinite" :class="[ item , animatedArr[index] ]"></view>
				<view>
					{{item}}
				</view>
				<view>
					{{animatedArr[index]}}
				</view>
			</view>

		</template>

		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				iconArr: ['lIcon-chart-1','lIcon-icon','lIcon-study','lIcon-js','lIcon-chart-2','lIcon-component',
							'lIcon-map-1','lIcon-form','lIcon-browse','lIcon-vue','lIcon-ts','lIcon-ts-2','lIcon-wechat','lIcon-poster','lIcon-rich','lIcon-css3',
					],
				animatedArr : [ 'bounce','flash','pulse','rubberBand','shake','headShake',
								'swing','tada','wobble','jello','heartBeat','hinge','jackInTheBox',
								'rollIn','zoomIn','flip']
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.content {
		text-align: center;
		display: flex;
		justify-content: start;
		flex-wrap: wrap;
		padding: 60rpx;
		.tabbar-icon {
			width: 33.33%;
			height: 100rpx;
			margin: 30rpx 0;
			font-size: 24rpx;
		}
		.icon {
			font-size: 50rpx;
		}
	}
</style>
