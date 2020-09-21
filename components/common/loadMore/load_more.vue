<template>
	<view class="load_more" >
		{{scrollBottomMsg}}
	</view>
</template>

<script>
	export default {
		props:{
			scrollBottomMsg:String
		}
	}
</script>

<style scoped>
	.load_more {
		text-align: center;
		color: #bcbcbc;
		padding: 20rpx 0;
	}
</style>
