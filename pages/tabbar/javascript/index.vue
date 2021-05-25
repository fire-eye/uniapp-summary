<template>
	<view class="js">
		<view class="title padding-sm text text-bold bg-gradual-blue">
			this
		</view>
		<view class="text-sm bg-white padding-sm">
			❏ 作为对象的方法调用。<br>
			❏ 作为普通函数调用。<br>
			❏ 构造器调用。<br>
			❏ Function.prototype.call或Function.prototype.apply调用。<br>
		</view>
		<view class="title padding-sm text text-bold bg-gradual-blue">
			call、apply
		</view>
		<view class="text-sm bg-white padding-sm">
			当使用call或者apply的时候，如果我们传入的第一个参数为null，函数体内的this会指向默认的宿主对象，在浏览器中则是window
		</view>
	</view>
</template>

<script>
	// 改变this指向
	var obj1 = {
		name : 'leonchua'
	}
	var obj2 = {
		name : 'fire-eye'
	}
	window.name = 'window Title'
	var getName = function(){
		if(!this) return;
		console.log('改变this指向',this,this.name)
	}
	getName()
	getName.call(obj1)
	getName.call(obj2)
	
	
	// 改变this指向
	
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			
		}
	}
</script>

<style>

</style>
