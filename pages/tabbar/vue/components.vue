<template>
	<view class="component">
		<view class="title padding-sm text text-bold bg-gradual-blue">
			简单自定义组件
		</view>
		<view class="text-blue text-center padding">
			<cshComponent>
				组件，你好！
			</cshComponent>
		</view>
		<view class="title padding-sm text text-bold bg-gradual-blue">
			作用域、缺省内容
		</view>
		<view class="text-blue text-center padding">
			<cshComponent>
				组件，你好！- {{name}}
			</cshComponent>
			<view class="padding">
				<cshComponent></cshComponent>
			</view>
		</view>
		<view class="title padding-sm text text-bold bg-gradual-blue">
			命名插槽
		</view>
		<view class="text-blue text-center padding">
			<cshComponentName>
				<template v-slot:header>
					加载的头部数据
				</template>
				<template v-slot:default>
					加载的内容数据
				</template>
				<template v-slot:footer>
					加载的底部数据
				</template>
			</cshComponentName>
			<view class="padding">
				<!-- v-slot:footer 缩略写法 -->
				<cshComponentName>
					<template #header>
						加载的头部数据 缩略写法
					</template>
					加载的内容数据 缩略写法
					<template #footer>
						加载的底部数据 缩略写法
					</template>
				</cshComponentName>
			</view>
		</view>
		
		<view class="title padding-sm text text-bold bg-gradual-blue">
			作用域插槽
		</view>
		<view class="text-sm bg-white padding-sm">
			父级插槽访问子组件数据，可以在子组件slot元素使用v-bind指令绑定一个prop
		</view>
		<view class="text-blue text-center padding">
			<view class="padding">
				<cshComponentButton>
					<template v-slot:default = "slotProps">
						{{slotProps.values.submit}}
					</template>
					<template v-slot:reset = "slotProps">
						{{slotProps.resets.reset}}
					</template>
				</cshComponentButton>
			</view>
			<view class="padding">
				<cshComponentButton>
					<template v-slot:default = "{values}">
						{{values.submit2}}
					</template>
					<template v-slot:reset = "{resets : subTitle}">
						{{subTitle.reset2}}
					</template>
				</cshComponentButton>
			</view>
		</view>
		
	</view>
	
</template>

<script>
	import cshComponent from '@/components/csh/csh-vue/csh-component.vue'
	import cshComponentName from '@/components/csh/csh-vue/csh-component-name.vue'
	import cshComponentButton from '@/components/csh/csh-vue/csh-component-button.vue'
	export default {
		components:{ cshComponent, cshComponentName, cshComponentButton },
		data() {
			const _url = '/pages/tabbar/vue/';
			return {
				name: '编译作用域',
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
