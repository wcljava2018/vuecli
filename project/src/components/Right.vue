<template>
	<div>
		<div v-if="value==1">
			<GoodsList :goodId="1"></GoodsList>
		</div>
		<div v-else-if="value==2">
			<GoodsList :goodId="2"></GoodsList>
		</div>
		<div v-else>
			<GoodsList :goodId="0"></GoodsList>
		</div>
	</div>
</template>

<script type="text/javascript">
	import Msg from './msg.js'
	import GoodsList from './goodsList.vue'
	export default{
		data(){
			return{
				value:0
			}
		},
		mounted:function(){
			var _this=this
			//_代表副本(行内规则) 前后this代表当前这个vue文件
			Msg.$on('val',function(m){				
				_this.value=m;
				//val是接收的那个val,写一个回调函数，接收到的val(1)交给m(1)了
			})
		},
		components:{
			GoodsList
		}
	}
</script>

<style>
</style>
