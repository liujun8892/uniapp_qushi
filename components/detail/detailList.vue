<template>
	<view class="flex commonList animate__animated animate__fadeInLeft animate__fast">
		<view class="userpic">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="content flex_colum">
			<view class="header flex_mBetween_asideCenter">
				<view class="flex_column">
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
					<view class="time">
						26天前
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
			<view class="title">
				<text>{{item.title}}</text>
			</view>
			<view class="main" :class="{'flex_center':item.isMovie}">
				<template v-if="item.isMedia">
					<template v-if="!item.isMovie">
							<block v-for="(item1,index1) in item.morePic" :key="index1">
								<image :src="item1" mode="widthFix" lazy-load class="morePic" @tap="previewMorePic(item.morePic,index1)"></image>
							</block>
					</template>
					<template v-else>
						<image :src="item.mediaPic" mode="widthFix" lazy-load></image>
					</template>				
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
		props: {
			item: Object,
			index: {
				type: Number,
				default: 0
			}
		},
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
				this.$emit('toggleAttention', this.index, true)
			},
			// 取消关注
			removeAttention() {
				uni.showToast({
					title: '取消关注',
					icon: 'success'
				});
				this.$emit('toggleAttention', this.index, false)
			},
			// 去详情页
			openDetail() {
				console.log('xq');
			},
			// 预览图片
			previewMorePic(pics,index){
				uni.previewImage({
					current: index,
					urls: pics,
					loop: true
				})
			}
		}
	}
</script>

<style scoped>
	/* 公共列表样式 */
	@import '/common/comom_list.css';

	.time {
		font-size: 25rpx;
		color: #d3d3d3;
	}
	
	.main image {
		height: 320rpx !important;
	}
</style>
