<template>
	<view class="vue">
		<view class="title padding-sm text text-bold bg-gradual-blue">
			{{title}} 
		</view>
		<view class="">
			<view class="padding">
				{{obj}}
				<button class="margin" type="primary" @tap="changeValBtn()">改变值</button>
			</view>
			<view class="padding">
				{{obj}}
				<button class="margin" type="primary" @tap="addValBtn()">添加属性</button>
				<button class="margin" type="warn" @tap="delValBtn()">删除属性</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '$set和$delete使用技巧',
				obj : {
					age : 30,
					class : '三班',
					school : '厦门大学'
				},
				numArr : [{
					title : '玩具',
					num : 10
				},
				{
					title : '书本',
					num : 5
				}
				]
			}
		},
		onLoad() {

		},
		methods: {
			addValBtn() {
				let test = {title : '添加了属性值'};
				let popArr=[];
				this.obj.human = 100;  //数据绑定对象不知道新增属性，无法监测到数据
				console.log(this.obj);
				this.$set( this.obj ,"add_propety", test); //监测到新增属性，数据改变
			},
			changeValBtn(){
				this.obj.age += 3; //非新增属性数据监测进行输出
			},
			delValBtn() {
				this.obj.add_propety.name = 'leonchua';  //数据绑定对象不知道新增属性，无法监测到数据
				console.log(this.obj.add_propety)
				this.$delete(this.obj.add_propety ,"title");// 删除对象title属性，同事监测出发属性变化,，数据改变
			}
		}
	}
</script>

<style>   
</style>
