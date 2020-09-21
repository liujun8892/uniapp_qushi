<template>
	<view class="nearly_update">
		<block v-for="(item,index) in update_list" :key="index">
			<view class="list_item flex animate__animated animate__fadeInLeft" @tap="openTopicDetail">
				<image :src="item.image" mode="widthFix" lazy-load ></image>
				<view class="content">
					<view class="content_title" >
						{{item.title}}
					</view>
					<view>
						<text space="ensp" class="topic_content">{{item.topic}}</text>
					</view>
					<view class="count">
						动态
						<text>{{item.newsNum}}</text>
						今日
						<text>{{item.todayNum}}</text>
					</view>
				</view>
			</view>
		</block>
	
	</view>
</template>

<script>
	export default {
		props: {
			update_list:Array,
		},
		methods: {
			openTopicDetail() {
				uni.navigateTo({
					url: '../../pages/topic-detail/topic-detail',				
				});
			}
		},
	}
</script>

<style scoped>
	.nearly_update {
		padding: 0 15rpx;
	}
	
	.list_item {
		padding: 24rpx 0 28rpx 0;
		border-bottom: 1rpx solid #EEEEEE;
	}
	
	.nearly_update .title {
		
	}
	
	.nearly_update image {
	
		margin-right: 28rpx;
		width: 180rpx;
		height: 180rpx;
		border-radius: 15rpx;
	
	}
	
	.content .content_title {
		font-size: 34rpx;
	}
	
	.topic_content {
		font-size: 32rpx;
		color: #9F9F9F;
	}
	
	.count {
		font-size: 28rpx;
		color: #9A9A9A;
	}
	
	.count text {
		display: inline-block;
		width: 80rpx;
		text-align: center;
	}
</style>
