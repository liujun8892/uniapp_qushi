<template>
	<view>
		<!-- 好友数据列表-->
		<block v-for="(item,index) in friendList" :key="index">
			<view class="body">
				<view class="flex_vertical_center commonList animate__animated animate__fadeInLeft animate__fast">
					<view class="userpic">
						<image :src="item.userpic" mode="widthFix" lazy-load></image>
					</view>
					<view class="header flex">
						<view class="left">
							<view class="username">
								<text>{{item.username}}</text>
							</view>
							<view class="usersex flex_center" :class="{'nvBgc':item.usersex===1}">
								<view class="icon iconfont" :class="item.usersex===0?'icon-nan':'icon-nv'">
								</view>
								<text>{{item.usersex===0?'男':'女'}}</text>
							</view>
						</view>
						<view class="right">
							<view :class="item.iconClass">
							</view>
						</view>
					</view>
				</view>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		props: {
			friendList: Array
		},
		data() {
			return {

			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.body {
		padding: 0 20rpx;
	}
	
	.header {
		flex: 1;
		justify-content: space-between;
	}
	
	.right {
		align-self: center;
	}
	
	.commonList {
		padding: 15rpx 0 20rpx 0;
		border-bottom: 1rpx solid #d8d8d8;
	}
	
	.commonList .userpic image {
		width: 110rpx;
		height: 110rpx;
		transform: translateY(5rpx);
		border-radius: 50%;
		margin-right: 22rpx;
	}
	
	
	.username>text {
		font-size: 33rpx;
	}
	
	
	.usersex {
		height: 32rpx;
		width: 75rpx;
		background-color: #44B3FF;
		border-radius: 32rpx;
		color: #FFFFFF;
		font-size: 24rpx;
	
	}
	
	.right view {
		width: 31rpx;
		height: 31rpx;
		color: #CCCCCC;
	}
	
	.nvBgc {
		background-color: pink;
	}
	
	
	.icon-zengjia1 {
		color: rgb(248,126,35) !important;
	}
</style>
