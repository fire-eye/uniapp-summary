<template>
	<view class="content">
		<map style="width: 100%; height:950rpx;" :latitude="latitude" :longitude="longitude" 
			:markers="markers" :scale="scale" :controls="controls"
			@controltap="controlbBtn"
			@regionchange="regionchangeBtn"
			>
		</map>
	</view>
</template>

<script>
	export default {
		data() {
		        return {
					id:0, // 使用 marker点击事件 需要填写id
		            title: 'map',
		            latitude: 0, //纬度
		            longitude: 0,//经度
		            markers: [], //标记点
					scale : 15, //缩放级别，5-18，default:16
					controls : [{
							id : 1,
							position : {
								left : 5,
								top: 40,
								width : 30,
								height : 30
							},
							iconPath : 'https://www.eme.cn/attachment/face/201811/pre_15421038255p4rm.png',
							clickable : true
						},
						{
							id : 2,
							position : {
								left : 5,
								top: 40 + 40,
								width : 30,
								height : 30
							},
							iconPath : 'https://www.eme.cn/attachment/face/201811/pre_15421038255p4rm.png',
							clickable : true
						}
					] //控件
		        }
		    },
		onLoad() {
			let location = uni.getStorageSync('location');
			if(location) {
				console.log('location')
				this.latitude = location.latitude;
				this.longitude = location.longitude;
				this.markers = [
					{
						latitude: this.latitude,
						longitude: this.longitude,
					},
					{
						latitude: this.latitude + 0.001,
						longitude: this.longitude + 0.001,
					},
					{
						latitude: this.latitude - 0.001,
						longitude: this.longitude - 0.001,
					},
					{
						latitude: this.latitude - 0.001,
						longitude: this.longitude + 0.001,
					},
					{
						latitude: this.latitude + 0.001,
						longitude: this.longitude - 0.001,
					},
				]
			}else{
				uni.getLocation({
					type:"gcj02 ",
					success(res) {
						let { latitude, longitude } = res;
						uni.setStorageSync( 'location',{
							latitude,
							longitude
						})
						// console.log(res,this.longitude)
					}
				})
			}

		},
		methods: {
			controlbBtn(e) { //点击控件时触发
				let { detail } = e;
				console.log('控件ID: ' , detail.controlId);
				if(detail.controlId == 1) {
					this.scale++
				}
				if(detail.controlId == 2) {
					this.scale--
				}
			},
			regionchangeBtn(e) { //视野发生变化时触发
				let { type , detail } = e;
				let causedBy = detail.causedBy;
				let centerLocation = detail.centerLocation;
				
				console.log('视野变化:',e,  '视野状态:',type ,' 视野模式:', causedBy,'视野变化中心点:',centerLocation);
				// if()
			}
		}
	}
</script>

<style scoped>
	.content {
		text-align: center;
		/* height: 400upx; */
		/* margin-top: 200upx; */
	}
</style>
