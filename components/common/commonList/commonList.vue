<template>
	<view class="flex commonList animate__animated animate__fadeInLeft animate__fast">
		<view class="userpic">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="content flex_colum">
			<view class="header flex_mBetween_asideCenter">
				<view class="left flex_center">
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
					<view class="user_opertor flex_vertical_center">
						<view class="flex_vertical_center attention" v-show="!item.isGuanZhu" @tap="addAttention(index)">
							<view class="icon iconfont icon-zengjia">
							</view>
							<text>关注</text>
						</view>
						<view class="delete icon iconfont icon-guanbi" v-show="item.isGuanZhu" @tap="removeAttention(index)">
						</view>
					</view>
				</view>
			</view>
			<view class="title" @tap="openDetail(item)">
				<text>{{item.title}}</text>
			</view>
			<view class="main flex_center">				
				<template v-if="item.isMedia">
					<image :src="item.mediaPic" mode="widthFix" lazy-load @tap="openDetail(item)"></image>
					<template v-if="item.isMovie">
						<view class="movie_play_controls icon iconfont icon-bofang">
						</view>
						<view class="movie_play_count flex_vertical_center">
							<text>20 次播放 2:47</text>
						</view>
					</template>					
				</template>
				<template v-if="item.isPicArticle">
					<view class="picArticle flex_vertical_center">
						<image :src="item.picArticleImg" mode="widthFix"></image>
						<text>{{item.picArticleTitle}}</text>
					</view>
				</template>
			</view>
			<view class="footer flex_mBetween_asideCenter">
				<view class="left flex_center">
					<text>{{item.address}}</text>				
				</view>
				<view class="right flex_center">
					<view class="item flex_center">
						<view class="icon iconfont icon-zhuanfa">						
						</view>
						<text>{{item.sharenum}}</text>
					</view>
					<view class="item flex_center">
						<view class="icon iconfont icon-pinglun1">						
						</view>
						<text>{{item.commentnum}}</text>
					</view>
					<view class="item flex_center">
						<view class="icon icon iconfont icon-ccdbaa">						
						</view>
						<text>{{item.likenum}}</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number
		}
		,
		data() {
			return {						
					
			}
		},
		methods: {
			addAttention(index) {
				uni.showToast({
					title: '关注',
					icon: 'success'
				});
				this.$emit('toggleAttention',this.index,true) 
			},
			// 取消关注
			removeAttention() {
				uni.showToast({
					title: '取消关注',
					icon: 'success'
				});
				this.$emit('toggleAttention',this.index,false) 
			},
			// 去详情页
			openDetail(item) {
				console.log(1);
				// uni.navigateTo({
				// 	url: 
				// });
				uni.navigateTo({
					url:`/pages/detail/detail?params=${JSON.stringify(item)}`,
				});
				// uni.navigateTo({
				// 	url: `  ../../../pages/detail/detail?params=${JSON.stringify(item)}`,
				// 	url:'../../../pages/detail/detail'
				// });
			}
		}
	}
</script>

<style scoped>
	.attention {
		/* margin-right: 23rpx; */
		padding: 0 10rpx;
		background-color: #F4F4F4;
	}

	.attention text {
		font-size: 26rpx;
		color: #444444;
	}

	.delete {
		font-size: 28rpx;
		color: #D5D5D5;
	}

	.commonList {
		padding: 20rpx;
	}

	.commonList .userpic image {
		width: 90rpx;
		border-radius: 50%;
		margin-right: 12rpx;
	}

	.username {
		margin-right: 10rpx;
	}

	.username>text {
		font-size: 28rpx;
		color:  #909090;
	}
	
	.content .header {
		height: 50rpx;
	}

	.content {
		flex: 1;	
		border-bottom: 1rpx solid #C0C0C0;
	}

	.flex_colum {
		display: flex;
		flex-direction: column;
	}

	.usersex {
		height: 32rpx;
		background-color: #44B3FF;
		padding: 0 10rpx;
		border-radius: 32rpx;
		color: #FFFFFF;
		font-size: 24rpx;

	}

	.title text {
		font-size: 32rpx;
	}

	.main {
		position: relative;
		margin: 15rpx 0;
	}
	.main image {
		width: 100%;
		border-radius: 20rpx;
	}
	
	.movie_play_controls {
		position: absolute;
		font-size: 130rpx;
		color: #FFFFFF;
	}
	
	.movie_play_count {
		position: absolute;
		right: 10rpx;
		bottom: 8rpx;
		height: 40rpx;
		color: #FFFFFF;
		background-color: rgba(51, 51, 51, 0.62);
		padding: 0 15rpx;
		border-radius: 40rpx;
	}
	
	.footer  {
		color: #B8B8B8;
		margin-bottom: 15rpx;
	}
	.footer .left text:nth-child(1) {
		margin-right: 7rpx;
	}
	
	.item {
		width: 80rpx;
	}
	.item .icon {
		font-size: 26rpx;
		margin-right: 5rpx;
	}
	
	.icon-ccdbaa {
		margin-top: -6rpx!important;
	}
	.picArticle {
		flex: 1;
		background-color: #F7F7F7;
		padding: 10rpx 20rpx 10rpx 5rpx;
		color: #454545;
		border-radius: 10rpx;
	}
	.picArticle image {
		width: 300rpx;
		margin-right: 30rpx;
	}
	.nvBgc {
		background-color: pink;
	}
</style>
