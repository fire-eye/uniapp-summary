<template>
	<view class="component">
		<view class="header">
			<slot name="header">头部</slot>
		</view>
		<view class="content">
			<slot>内容</slot>
		</view>
		<view class="footer">
			<slot name="footer">底部</slot>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
		}
	}
</script>

<style lang="scss" scoped>   

</style>
