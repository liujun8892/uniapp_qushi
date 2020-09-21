<template>
	<view class="hot_categories">
		<view class="title flex_mBetween_asideCenter">
			<text>热门分类</text>
			<view class="more flex" @tap="openTopic">
				<text>更多 </text>
				<view class="icon iconfont icon-jinru"></view>
			</view>
		</view>
		<view class="tags">
			<text>最新</text>
			<text>游戏</text>
			<text>情感</text>
			<text>打卡</text>
			<text>故事</text>
			<text>最爱</text>
		</view>
	</view>
</template>

<script>
	export default {
		methods:{
			openTopic() {
				uni.navigateTo({
					url: '../../pages/topic/topic'	
				})
			}
		}
	}
</script>

<style scoped>
	.hot_categories {
		margin-top: 25rpx;
		padding: 0 15rpx;
		border-top: 1rpx solid #dadada;
		border-bottom: 1rpx solid  #dadada;
	}
	
	.hot_categories {
		padding: 0 15rpx;
		font-size: 28rpx;
	}
	
	.hot_categories .title {
		font-size: 30rpx;
		margin: 26rpx 0;
	}
	
	.more text {
		color: #D3D3D3;
	}
	
	.more {
		color: #D3D3D3;
	}
	
	.hot_categories .tags {
		margin-bottom: 35rpx;
		display: flex; 
		justify-content: space-evenly;
		/* padding: 0 20rpx; */
		
	}
	
	.tags text {
		background-color: #F7F7F7;
		padding: 10rpx 20rpx;
		border-radius: 15rpx;
		color: #A2A2A2;
	}
</style>
