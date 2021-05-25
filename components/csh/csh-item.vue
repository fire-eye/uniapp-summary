<template>
	<view class="csh-item">
		<view class="title padding-sm text text-bold bg-gradual-blue">
			{{title}}
		</view>
		
		<view class="text-sm bg-white padding-sm" v-if="isShow">
			<slot></slot>
		</view>
	</view>
</template>

<script>

	export default {
		props: {
			type: {
				type: String,
				default: ''
			},
			title: {
				type: String,
				default: ''
			},
			isShow: {
				type: Boolean,
				default: true
			}
		},
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
