<template>
	<!-- 底部的固定信息输入框 -->
	<view class="bottom_msg_box flex_vertical_center">
		<!-- 输入框 -->
		<input type="text" v-model="text" placeholder="文明发言" />
		<!-- 发送信息字体图标 -->
		<view class="icon iconfont icon-fabu" @tap="sumbit">	
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text: ''
			}
		},
		methods: {
			sumbit() {
				this.$emit('sendMsg',this.text)
				this.text=''
			}
		},
	}
</script>

<style scoped>
	/* 底部输入框样式 */
	.bottom_msg_box {
		position: fixed;
		left: 0;
		right: 0;
		bottom: 0;
		height: 100rpx;
		padding: 0 20rpx;
		border-top: 1rpx solid #F8F8F8;
	}
	
	.bottom_msg_box input {
		flex: 6;
		height: 60rpx;
		padding: 0 0 0 20rpx;
		background-color: #F7F7F7;
		font-size: 28rpx;
		border-radius: 15rpx;
	}
	
	.icon-fabu {
		flex: 1;
		width: 80rpx;
		font-size: 48rpx;
		text-align: center;
	}
</style>
