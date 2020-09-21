<template>
	<view>
		<!-- 导航栏模糊背景 -->
		<view class="nav_bgc">
			<image :src="topicInfo.navImg" mode="aspectFill"></image>
		</view>
		<!-- 主体内容区域 -->
		<view class="main_content">
			<!-- 标题 -->
			<view class="tpDet_title flex">
				<image :src="topicInfo.titleImg" mode="widthFix"></image>
				<text>#{{topicInfo.title}}#</text>
			</view>
			<!-- 数据统计 -->
			<view class="tpDet_count">
				动态
				<text>{{topicInfo.newsNum}}</text>
				今日
				<text>{{topicInfo.todayNum}}</text>
			</view>
			<!-- 话题 -->
			<view class="tpDet_topic">
				{{topicInfo.topic}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			topicInfo: Object
		}
	}
</script>

<style scoped>
	.nav_bgc {
		width: 100%;
		height: 300rpx;
	}

	.nav_bgc image {
		width: 100%;
		height: 100%;
		filter: blur(10px);
	}

	.main_content {
		padding: 0 15rpx;
	}

	.tpDet_title {
		position: relative;
	}

	.tpDet_title image {
		position: absolute;
		top: -75rpx;
		width: 150rpx;
		height: 150rpx;
		border-radius: 15rpx;
	}

	.tpDet_title text {
		margin-left: 170rpx;
		flex: 1;
		font-size: 34rpx;
	}

	.tpDet_count {
		margin: 40rpx 0 35rpx 0;
		color: #CBCBCB;
		font-size: 29rpx;
	}

	.tpDet_count text {
		display: inline-block;
		width: 80rpx;
		text-align: center;

	}

	.tpDet_topic {
		color: #A7A7A7;
		font-size: 33rpx;
	}
</style>
