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
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 公共样式 */
	 @import './common/uni.css';
	 /* 阿里字体图标 */
	 @import './common/icon.css';
	 /* animate.css */
	 @import './common/animate.css';
	 /* 导入公共样式 */
	 @import './common/common.css';
	 
	 ::-webkit-scrollbar {  
	     display: none;  
	     width: 0 !important;  
	     height: 0 !important;  
	     -webkit-appearance: none;  
	     background: transparent;  
	 }
	 
</style>
