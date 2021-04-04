<template>
	<view class="component-input">
		<input v-model="content" class="padding-left-sm">
	</view>
</template>

<script>

	export default {
		data() {
			return {
				content: 'Vue.js无难事'
			}
		},
		methods: {
		}
	}
</script>

<style lang="scss" scoped>   
input {
	border : 1px solid #eee;
	height: 40px;
	line-height: 40px;
	
	&::before{
		border-radius: 0;
		padding: 0;
		margin: 0;
	}
}
</style>
