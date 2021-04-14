<template>
	<view class="es6">
		<view class="title padding-sm text text-bold bg-gradual-blue">
			{{title}} 
		</view>
		<view class="padding bg-white">
			for...in缺点。 <br>
			数组的键名是数字，但是 for...in 循环是以字符串作为键名“0”、“1”、“2”等等。 <br>
			for...in 循环不仅遍历数字键名，还会遍历手动添加的其他键，甚至包括原型链上的键。 <br>
			某些情况下， for...in 循环会以任意顺序遍历键名。 <br>
		</view>
		<view class="padding bg-grey">
			for...of优点 <br>
			有着同 for...in 一样的简洁语法，但是没有 for...in 那些缺点。 <br>
			不同于 forEach 方法，它可以与 break 、 continue 和 return 配合使用。 <br>
			提供了遍历所有数据结构的统一操作接口。 <br>
		</view>
		<view class="padding bg-cyan">
			三次解构赋值 <br>
			const node = { loc: { start: { line: 1, column: 5 } } };<br>
			let { loc, loc: { start }, loc: { start: { line }} } = node;<br>
			line // 1<br>
			loc  // Object {start: Object}<br>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'ES6教程'
			}
		},
		onLoad() {
			// for...in 循环有几个缺点。
			// 数组的键名是数字，但是 for...in 循环是以字符串作为键名“0”、“1”、“2”等等。
			// for...in 循环不仅遍历数字键名，还会遍历手动添加的其他键，甚至包括原型链上的键。
			// 某些情况下， for...in 循环会以任意顺序遍历键名。
			// *************************************
			// for...of优点
			// 有着同 for...in 一样的简洁语法，但是没有 for...in 那些缺点。
			// 不同于 forEach 方法，它可以与 break 、 continue 和 return 配合使用。
			// 提供了遍历所有数据结构的统一操作接口。
			
			
			const arr = ['red', 'green', 'blue'];
			for(let v of arr) {
			  console.log(v); // red green blue
			}
			const obj = {};
			obj[Symbol.iterator] = arr[Symbol.iterator].bind(arr);
			for(let v of obj) {
			  console.log(v); // red green blue
			}
			console.log('对象遍历,并break操作')
			let arrayLike = { name : 'leonchua',length: 2, 0: 'a', 1: 'b' };
			for( let item of Object.keys(arrayLike) ) {
				console.log('arrayLike',item , arrayLike[item])
				if(item === 'name') break; //key值等于name ,跳出，这里没输出length : 2
			}
			
			
			// proxy代理器
			var proxy = new Proxy({ a : 1 }, {
			  get: function(target, propKey) {
				  console.log( 'setting' ,target, propKey)
			    return 35;
			  },
			  set : function(target, propKey, value, ) {
				   console.log(`setting ${propKey}!`);
				  return Reflect.set(target, propKey, value, receiver);
			  }
			});
			
			console.log(proxy.time , proxy.name, proxy.title)
			
			// 三次解构赋值
			const node = {
			  loc: {
			    start: {
			      line: 1,
			      column: 5
			    }
			  }
			};
			let { loc, loc: { start }, loc: { start: { line }} } = node;
			console.log(line, loc, start);
		},
		methods: {

		}
	}
</script>

<style>   
	.content {
		text-align: center;
		height: 400upx;
		margin-top: 200upx;
	}
</style>
