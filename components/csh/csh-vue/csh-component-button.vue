<template>
	<view class="component">
		<button class="submit" type="primary">
			<slot name="default" :values="subTitle">{{subTitle.submit}}</slot>
		</button>
		<button class="reset" type="default">
			<slot name="reset" :resets="subTitle">{{subTitle.reset}}</slot>
		</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				subTitle : {
					submit : '提交数据',
					submit2 : '登录',
					reset : '重置数据',
					reset2 : '注册'
				}
			}
		},
		methods: {
		}
	}
</script>

<style lang="scss" scoped>   

</style>
