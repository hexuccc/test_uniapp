<template>
	<view>
		<view>
			<wxswiper></wxswiper>
		</view>
	</view>
</template>

<script>
	import wxswiper from '../../wxcomponents/wxswiper/index.vue'
	export default{
		data(){
			return{
				name:'首页'
			}
		},
		components:{
			wxswiper
		}
		
	}
</script>

<style>
</style>
