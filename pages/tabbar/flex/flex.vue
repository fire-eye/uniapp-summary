<template>
	<view class="content">
		<view class="title">
			垂直居中
		</view>
		<view class="box">
			<view class="left">
				<view class="center">
					左
				</view>
			</view>
			<view class="mid">
				<view class="center">
				中
				</view>
			</view>
			<view class="right">
				<view class="center">
				右
				</view>
			</view>
		</view>
		
		<view class="title">
			左右布局
		</view>
		<view class="box-lr">
			<view class="left">
				<view class="center">
					<view class="left">
						左
					</view>
					<view class="right">
						右
					</view>
				</view>
			</view>
			<view class="right">
				<view class="center">
				右
				</view>
			</view>
		</view>
		
		<view class="title">
			flex属性
		</view>
		<view class="desc">
			flex | [ <'flex-grow':空间剩余放大> <'flex-shrink':空间不足缩小>? || <'flex-basis'> ]
		</view>
		<view class="box-auto">
			<view class="left">
				<view class="center">
					左
				</view>
			</view>
			<view class="right">
				<view class="center">
				右
				</view>
			</view>
		</view>
		
		<view class="title">
			align-self属性:	允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。
		</view>
		<view class="desc">
			auto | flex-start | flex-end | center | baseline | stretch; 
		</view>
		<view class="box-align-self">
			<view class="left">
				<view class="center">
					左
				</view>
			</view>
			<view class="mid">
				<view class="center">
				中
				</view>
			</view>
			<view class="right">
				<view class="center">
				右
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
		
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		height: auto;
		.title {
			padding: 20rpx;
			font-size: 30rpx;
			font-weight: 600;
		}
		.desc {
			font-size: 24rpx;
			color: #666;
			padding: 0 20rpx 30rpx;
		}
		.box {
			width: 100%;
			display: flex;
			.left,.mid,.right{
				width: 33.33%;
				height: 100rpx;
				background-color: #f1f1f1;
				display: flex;
				justify-content: center;
				align-items: center;
			}
			.mid {
				background-color: #ddd;
			}
		}
		
		.box-lr {
			width: 100%;
			display: flex;
			justify-content: space-between;
			.left,.right{
				width: 33.33%;
				height: 100rpx;
				background-color: #f1f1f1;
				display: flex;
				justify-content: center;
				align-items: center;
				.center {
					display: flex;
					justify-content: center;
					width: 100%;
					.left, .right {
						width: 50%;
						background-color: #ddd;
					}
					.right {
						background-color: #ccc;
					}
				}
			}
		}
		
		.box-auto {
			width: 100%;
			display: flex;
			.left,.right{
				width: 33.33%;
				height: 100rpx;
				background-color: #f1f1f1;
				display: flex;
				justify-content: center;
				align-items: center;
				.center {
					display: flex;
					justify-content: center;
					width: 100%;
				}
			}
			.right {
				flex: 1;
				background-color: #ddd;
			}
		}
		
		.box-align-self {
			width: 100%;
			height: 200rpx;
			background-color: #f8f8f8;
			display: flex;
			.left,.mid,.right{
				width: 33.33%;
				height: 100rpx;
				background-color: #f1f1f1;
				display: flex;
				justify-content: center;
				align-items: center;
			}
			.mid {
				background-color: #ddd;
				align-self: flex-end ;
			}
		}
	}
</style>
