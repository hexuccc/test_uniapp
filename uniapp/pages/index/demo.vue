<template>
	<view class="content">
		<!-- <image src="../../static/g1.gif" mode="widthFix"></image> -->
		<text class="title">鹊伴相依间，佳期又一年</text>
		<text class="title">做我女朋友吧！</text>
		<view class="operate">
			<button type="primary" class="btn" @tap="agree">好呀</button>
			<button type="warn" class="btn" @tap="disagree">不好</button>
		</view>
		<view class="message" v-for="one in love":key="one">{{one}}</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				love:[],
				timer:{}
			}
		},
		onLoad() {
			this.back=uni.getBackgroundAudioManager()
			this.back.src="http://140.143.132.225/love/pdd.mp3"
			this.back.title="音乐"
			this.back.play()
		},
		onShow(){
			this.love=[]
			this.timer={}
			let msg={
				2000: "我爱你！",
				4000: " I love you! (英语)",
				6000: "愛しています (日语)",
				8000: " ich liebe dich! (德语)",
				10000: "я люблю тебя! (俄语)",
				12000: "ti amo! (意大利语)",
				14000: "te amo! (西班牙语)",
				16000: "나 사랑해요! (韩语)",
				18000: "jeg elsker dig! (丹麦语)",
				20000: "σ 'αγαπώ! (希腊语)"
			} 
			let ref=this;
			for(let key in msg){
				let t=setTimeout(function(){
					ref.love.push(msg[key])
					delete ref.timer[key]
				},key)
				ref.timer[key]=t
			}
		},
		onHide:function(){
			for(let key in this.timer){
				clearTimeout(this.timer[key])
			}
		},
		methods: {
             agree:function(){
				 uni.showToast({
				 	icon:"none",
					title:"我就知道你一定会同意",
					duration:4000
				 })
			 },
			 disagree:function(){
				 uni.showModal({
				 	title:"要不要当我女朋友",
					content:"（：",
					cancelText:"拒绝",
					confirmText:"同意",
					success:function(res){
						if(res.confirm){
							uni.showToast({
								icon:"none",
								title:"我就知道你一定会同意",
								duration:4000
							})
						}
						else{
							uni.showToast({
								icon:"none",
								title:"你错过了一个亿",
								duration:4000
							})
						}
					}
				})
			 }
		}
	}
</script>

<style lang="less">
	@import url("./index.less");
	
</style>
