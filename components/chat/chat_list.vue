<template>
	<view class="chat_box">
		<block v-for="(item, index) in chatMsgList" :key="index">
			<!-- 聊天数据展示 -->
			<template v-if="item.formatTime">
				<!-- 时间间隔大于5分钟显示 -->
				<view class="time">
					{{item.formatTime}}
				</view>
			</template>
			
			<view class="chat_list_box flex" :class="{'me_loyout':item.isMe}">
				<!-- 对方用户头像 -->
				<template v-if="!item.isMe">
					<image :src="item.friendPic" mode="widthFix" lazy-load></image>
				</template>				
				<!-- 聊天内容 -->
				<view class="chat_content_box flex_center" :class="{'content_img':item.isMe,'padding30':!item.isText}">
					<!-- 发送的是文字 -->
					<template v-if="item.isText">
						<text>{{item.sendText}}</text>
					</template>					
					<!-- 发送的是图片 -->
					<template v-if="!item.isText">
						<image :src="item.sendPic" mode="widthFix" lazy-load></image>
					</template>					
				</view>
				<!-- 我方用户头像 -->
				<template v-if="item.isMe">
					<image :src="item.myPic" class="myPic" mode="widthFix" lazy-load></image>
				</template>				
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		props: {
			chatMsgList: {
				type: Array
			},
		},
	}
</script>

<style scoped>
	.chat_box {
		padding: 0 30rpx;
	}
	
	.chat_list_box {
		padding: 20rpx 0;
	}
	
	.chat_list_box>image {
		flex-shrink: 0;
		margin-right: 35rpx;
		width: 80rpx;
		height: 90rpx;
		border-radius: 50%;
	}
	
	.chat_list_box .chat_content_box {
		position: relative;
		margin-right: 100rpx;
		background-color: #F4F4F4;
		font-size: 29rpx;
		padding: 20rpx;
		border-radius: 20rpx;
	}
	
	.chat_content_box::after {
		position: absolute;
		left: -30rpx;
		top: 30rpx;
		border: 16rpx solid #F4F4F4;
		content: "";
		border-color: transparent #F4F4F4 transparent transparent;
	
	}
	
	.chat_box .chat_list_box .padding30 {
		padding-bottom: 30rpx;
	}
	
	.chat_content_box image {
		width: 300rpx;
	}
	
	.chat_box .me_loyout {
		justify-content: flex-end;
	}
	
	.chat_box .chat_list_box .myPic {
		margin: 0;
	}
	
	.chat_box .chat_list_box .content_img {
		margin-right: 35rpx;
		margin-left: 100rpx;
	}
	
	.chat_box .chat_list_box .content_img::after {
		left: auto;
		right: -30rpx;
		border-color: transparent transparent transparent #F4F4F4;
	}
	
	.time {
		text-align: center;
		color: #D5D5D5;
		font-size: 24rpx;
	}
</style>
