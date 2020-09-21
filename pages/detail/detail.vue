<template>
	<view>
		<!-- 详情数据 -->
		<detail-list :item="detailItem" @toggleAttention="toggleAttention"></detail-list>

		<!-- 评论 -->
		<view class="u-comment-title">最新评论 {{comment.count}}</view>
		<view class="uni-comment u-comment">
			<block v-for="(item,index) in comment.list" :key="index">
				<comment-list :item="item" :index="index"></comment-list>
			</block>
		</view>

		<!-- 底部占位盒子 -->
		<view style="height: 100upx;"></view>

		<!-- 输入框 -->
		<user-chat-bottom @sendMsg="submit" style="background-color: #FFFFFF;"></user-chat-bottom>

		<!-- 分享 -->
		<more-share :show="shareshow" @togle="togle"></more-share>
	</view>
</template>

<script>
	// 导入公共样式列表
	import detailList from '../../components/detail/detailList.vue'
	// 导入评论逐渐
	import commentList from "../../components/detail/comment_list.vue";
	// 导入评论js
	import time from "../../common/time.js";
	// 导入输入组件
	import userChatBottom from "../../components/chat/chat_input.vue";
	// 导入分享组件
	import moreShare from "../../components/common/more-share.vue";
	export default {
		// 挂载组件
		components: {
			detailList,
			commentList,
			userChatBottom,
			moreShare
		},
		data() {
			return {
				// 分享显示
				shareshow: false,
				// 详情数据
				detailItem: {},
				// 评论数据
				comment: {
					count: 20,
					list: []
				},
			}
		},
		onLoad(e) {
			let detailObj = JSON.parse(e.params)
			detailObj.morePic = [detailObj.mediaPic, 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
				'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/2.jpg'
			]
			this.detailItem = detailObj
			this.initPageSetting(this.detailItem.title)
			this.getcomment();
		},
		onNavigationBarButtonTap(e) {
			if (e.index === 0) {
				this.togle();
			}
		},
		methods: {
			// 动态设置导航栏标题
			initPageSetting(navTile) {
				uni.setNavigationBarTitle({
					title: navTile
				})
			},
			// 切换关注状态
			toggleAttention(index, status) {
				this.detailItem.isGuanZhu = status
			},
			// 获取评论
			getcomment() {
				let arr = [
					// 一级评论
					{
						id: 1,
						fid: 0,
						userpic: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
						username: "小猫咪",
						time: "1555400035",
						data: "支持国产，支持DCloud!",
					},
					// 子级评论
					{
						id: 2,
						fid: 1,
						userpic: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
						username: "小猫咪",
						time: "1555400035",
						data: "支持国产，支持DCloud!",
					},
					{
						id: 3,
						fid: 1,
						userpic: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
						username: "小猫咪",
						time: "1555400035",
						data: "支持国产，支持DCloud!",
					},
					{
						id: 4,
						fid: 0,
						userpic: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
						username: "小猫咪",
						time: "1555400035",
						data: "支持国产，支持DCloud!",
					},
				];
				for (let i = 0; i < arr.length; i++) {
					arr[i].time = time.gettime.gettime(arr[i].time);
				}
				this.comment.list = arr;
			},
			// 发表评论
			submit(data) {
				let obj = {
					id: 1,
					fid: 0,
					userpic: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
					username: "小猫咪",
					time: time.gettime.gettime(new Date().getTime()),
					data: data,
				};
				this.comment.list.push(obj);
			},
			// 切换分享显示隐藏
			togle() {
				this.shareshow = !this.shareshow
			},
		}
	}
</script>

<style>
	/* 评论 */
	.u-comment {
		padding: 0 20upx;
	}

	.u-comment-title {
		padding: 20upx;
		font-size: 30upx;
		font-weight: bold;
	}
</style>
