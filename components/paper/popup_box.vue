<template>
	<!-- 弹出框 -->
	<!-- 遮盖层 -->
	<view class="mask" v-show="popupShow" @tap="hidePopup">
		<view class="popup_box">
			<!-- 加糗友 -->
			<view class="flex_vertical_center" hover-class="greyBgc" @tap="addFriend">
				<view class="icon iconfont icon-sousuo">
				</view>
				加糗友
			</view>
			<!-- 清除未读 -->
			<view class="flex_vertical_center" hover-class="greyBgc" @tap="clearNoRead">  
				<view class="icon iconfont icon-qingchu">
				</view>
				清除未读
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			popupShow:{
				type:Boolean,
				default:false
			}
		},
		methods:{
			hidePopup(){
				this.$emit('hidePopup')
			},
			addFriend(){
				this.$emit('addFriend')
			},
			clearNoRead(){
				this.$emit('clearNoRead')
			},
		}
	}
</script>

<style scoped>
	.popup_box {
		position: fixed;
		right: 0;
		top: 10upx;
		width: 50%;
		box-shadow: 1rpx 1rpx 20rpx 2rpx #CCCCCC;
		background-color: #FFFFFF;
		z-index: 2000;
	}
	
	.popup_box .icon {
		margin: 0 20rpx 0 24rpx;
	}
	
	.flex_vertical_center {
		font-size: 35rpx;
		padding: 30rpx 0;
	}
	
	.flex_vertical_center:nth-of-type(2) {
		padding-top: 15rpx;
	}
	
	.mask {
		position: fixed;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		z-index: 1999;
	}
	
	.greyBgc {
		background-color: #e4e3e8;
	}
</style>
