<template>
	<view class="vue">
		<view class="title padding-sm text text-bold bg-gradual-blue">{{ title }}</view>
		<view class="content">
			<view class="flex">
				<button v-for="tab in tabs" :key="tab.title" :class="['tab-button', { active: currentTab === tab.title }]" @click="currentTab = tab.title">
					{{ tab.displayName }}
				</button>
			</view>

			<keep-alive><component v-bind:is="currentTabComponent" class="tab bg-white"></component></keep-alive>
		</view>
	</view>
</template>

<script>
import Vue from 'vue';
import cshComponent from '@/components/csh/csh-vue/csh-component.vue';
import cshComponentName from '@/components/csh/csh-vue/csh-component-name.vue';
import cshComponentButton from '@/components/csh/csh-vue/csh-component-button.vue';
import cshComponentInput from '@/components/csh/csh-vue/csh-component-input.vue';
export default {
	components: { cshComponent, cshComponentName, cshComponentButton, cshComponentInput },
	data() {
		return {
			title: '动态组件',
			currentTab: 'cshComponentInput',
			tabs: [
				{ title: 'cshComponentInput', displayName: '图书介绍' },
				{ title: 'cshComponent', displayName: '图书评价' },
				{ title: 'cshComponentName', displayName: '图书问答' }
			]
		};
	},
	onLoad() {},
	methods: {
		url(data) {
			uni.navigateTo({
				url: data
			});
		}
	},
	computed: {
		currentTabComponent: function() {
			console.log(this.currentTab);
			return this.currentTab;
		}
	}
};
</script>

<style lang="scss" scoped>
.vue {
	div {
		width: 400px;
	}
	.tab-button {
		width: 33.33%;
		padding: 6px 10px;
		border-top-left-radius: 3px;
		border-top-right-radius: 3px;
		cursor: pointer;
		background: #f0f0f0;	
		margin: 5px;
	}
	.tab-button:hover {
		background: blue;
	}
	.tab-button.active {
		background: #007AFF;
		color: #fff;
	}
	.tab {
		border: solid 1px #ccc;
		padding: 20px;
	}
}
</style>
