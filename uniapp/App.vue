<!-- @import './wxcomponents/wxswiper/index.vue' -->
<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		onError(e) {
			console.log('error',e)
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
