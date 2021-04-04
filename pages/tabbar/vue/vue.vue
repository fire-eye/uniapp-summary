<template>
	<view class="vue">
		<view class="title padding-sm text text-bold bg-gradual-blue">
			{{title}}
		</view>
		<view class="lists">
			<template v-for="( item, index ) in lists">
				<view class="list flex padding" @tap="url(item.url)">
					<view class="flex justify-center align-center img margin-right-sm bg-gradual-blue text-xsl radius">
						{{index + 1}}
					</view>
					<view class="list-content flex-sub">
						<view class="title text-bold">
							{{item.title}}
						</view>
						<view class="desc text-gray">
							{{item.content}}
						</view>
					</view>
				</view>
			</template>
			
		</view>
	</view>
</template>

<script>
	import Vue from 'vue'
	Vue.component('tab-introduce', {
		data(){
			return {
				content: 'Vue.js无难事'
			}
		},
		template: '<div><input v-model="content"></div>'
	})
	Vue.component('tab-comment', { 
		template: '<div>这是一本好书</div>' 
	})
	Vue.component('tab-qa', { 
		template: '<div>有人看过吗？怎么样？</div>' 
	})
	export default {
		data() {
			const _url = '/pages/tabbar/vue/';
			return {
				title: 'Vue教程与案例',
				lists : [
					{
						title : '组件插槽分发内容',
						url : _url + 'components',
						content : '组件开发最常用的插槽分发内容教程与案例运用'
					},
					{
						title : 'Vuex',
						url : _url + 'vuex',
						content : 'vuex教程与教程案例运用'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			url(data){
				uni.navigateTo({
					url:data
				})
			}
		}
	}
</script>

<style lang="scss" scoped>   
.vue {
	.lists {
		background-color: #fff;
		.list {
			border-bottom: 1rpx solid #dedede;
			line-height: 42rpx;
		}
		.img {
			width: 120rpx;
			height: 120rpx;
			image {
				width: 100%;
				height: 100%;
			}
		}
	}
}
</style>
