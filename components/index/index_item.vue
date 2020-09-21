<template>
	<view class="list-item animate__animated animate__zoomIn">
		<view class="list-item-header flex_mBetween_asideCenter">
			<view class="user_info flex_vertical_center">
				<image :src="items.userpic" mode="widthFix" lazy-load></image>
				<text>{{items.username}}</text>
			</view>
			<view class="user_opertor flex_vertical_center">
				<view class="flex_vertical_center attention" v-show="!isGuanZhu" @tap="addAttention">
					<view class="icon iconfont icon-zengjia">
					</view>
					<text>关注</text>
				</view>
				<view class="delete icon iconfont icon-guanbi" v-show="isGuanZhu" @tap="removeAttention">
				</view>
			</view>
		</view>
		<view class="list-item-title" @tap="openDetail">
			{{items.title}}
		</view>
		<view class="flex_center list-item-content">
			<image :src="items.coverPic" mode="widthFix" lazy-load @tap="openDetail"></image>
			<template v-if="items.type==='movie'">
				<view class="movie_play_controls icon iconfont icon-bofang">
				
				</view>
				<view class="movie_play_count flex_vertical_center">
					<text>{{items.playNum}} 次播放 {{items.playTime}}</text>
				</view>
			</template>			
		</view>
		<view class="flex_mBetween_asideCenter list-item-comment">
			<view class="flex user_like">
				<view :class="['flex_vertical_center','like',items.userLike.flag===1?'active':'']">
					<view class="icon iconfont icon-icon_xiaolian-mian" @tap="likeHandle(1)">
					</view>
					<text>{{items.userLike.likeNum}}</text>
				</view>
				<view :class="['flex_vertical_center','disLike',items.userLike.flag===2?'active':'']" >
					<view class="icon iconfont icon-kulian" @tap="likeHandle(2)">
					</view> 	
					<text>{{items.userLike.disLikeNum}}</text>
				</view>
			</view>
			<view class="flex user_share">
				<view class="flex_vertical_center user_share_comment">
					<view class="icon iconfont icon-pinglun1">
					</view>
					<text>{{items.commentNum}}</text>
				</view>
				<view class="flex_vertical_center user_share_forward">
					<view class="icon iconfont icon-zhuanfa">
					</view>
					<text>{{items.shareNum}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item:Object,
			index:Number
		},
		data() {
			return {
				isGuanZhu: this.item.isGuanZhu,
				items:this.item
			}
		},
		methods:{
			// 关注
			addAttention() {
				uni.showToast({
				    title: '关注',
				    icon: 'success'
				});
				this.isGuanZhu = true
			},
			// 取消关注
			removeAttention() {
				uni.showToast({
				    title: '取消关注',
				    icon: 'success'
				});
				this.isGuanZhu =false
			},
			// 用户喜好
			likeHandle(type) {
				// 重复点击返回
				if(this.items.userLike.flag===type) return
				// 计算用户喜好数量
				type===1?this.items.userLike.likeNum++:this.items.userLike.disLikeNum++
				this.items.userLike.flag = type
				// 如果用户已操作相对应的数量需要--
				if(this.items.userLike.flag!==0){
					type===1?this.items.userLike.disLikeNum--:this.items.userLike.likeNum--
				}
			},
			// 取详情页
			openDetail(){
				uni.navigateTo({
					url: `../../pages/detail/detail?params=${JSON.stringify(this.item)}`
				});
			}
		}
	}
</script>

<style scoped>
	.list-item {
		padding: 20rpx;
		border-bottom: 1rpx solid #ccc;
	}
	
	.user_info>image {
		width: 75rpx;
		border-radius: 50%;
		margin-right: 15rpx;
	}
	
	.user_info>text {
		font-size: 28rpx;
		color: #9C9C9C;
	}
	
	
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
	
	.list-item-title {
		margin: 15rpx 0;
		font-size: 32rpx;
	}
	
	.list-item-content image {
		width: 100%;
		border-radius: 20rpx;
	}
	
	.list-item-comment {
		color: #9C9C9C;
		margin: 10rpx 0 20rpx;
	}
	
	.list-item-comment text {
		padding: 0 15rpx;
	}
	
	.list-item-content {
		position: relative;
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
	
	.user_like .active {
		color: #F0AD4E;
	}
	
	.user_like .like {
		width: 110rpx;
	}
</style>
