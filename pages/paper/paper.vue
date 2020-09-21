<template>
	<view class="paper">
		<paper-list :paparList="paparList"></paper-list>
		<!-- 子组件加载更多 -->
		<load-more :scrollBottomMsg="scrollBottomMsg"></load-more>
		<!-- 弹出框 -->
		<popup-box :popupShow="popupShow" @hidePopup="hidePopup" @addFriend="addFriend" @clearNoRead="clearNoRead"></popup-box>
	</view>
</template>

<script>
	// 导入小纸条数据列表组件
	import paperList from '../../components/paper/paper_list.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	// 导入弹出框组件
	import popupBox from '../../components/paper/popup_box.vue'
	export default {
		components: {
			paperList,
			loadMore,
			popupBox
		},
		data() {
			return {
				// 弹出框显示隐藏
				popupShow: false,
				scrollBottomMsg: '下拉加载更多',
				paparList: [{
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/11.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/6.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/5.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}]
			}
		},
		methods: {
			getData() {
				// 获取数据
				let newList = [{
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/1.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/2.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 12
				}, {
					userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
					username: 'JIA一勺',
					time: '13:58',
					content: '赵丽颖《知否》一句话打脸，“读书...',
					contentNum: 0
				}]
				// 刷新数据
				this.paparList = newList
			},
			// 加载更多数据
			async loadMore() {
				// 如果不是加载更多状态,返回
				if (this.scrollBottomMsg !== '下拉加载更多') return
				// 加载中
				this.scrollBottomMsg = '正在加载数据...'
				// 模拟加载数据
				await setTimeout(() => {
					let itemObj = {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/8.jpg',
						username: '清华博士',
						time: '13:58',
						content: '分享时间管理',
						contentNum: 18
					}
					for (var i = 0; i < 5; i++) {
						this.paparList.push(itemObj)
					}
				}, 300)
				// 加载完成
				this.scrollBottomMsg = '下拉加载更多'
			},
			// 隐藏弹出框
			hidePopup() {
				this.popupShow =false
			},
			// 加糗友
			addFriend() {
				console.log('加糗友');
				this.hidePopup()
			},
			//清除未读
			clearNoRead(){
				console.log('清除未读');
				this.hidePopup()
			}
		},
		// 监听下拉刷新数据
		onPullDownRefresh() {
			setTimeout(() => {
				this.getData()
				uni.stopPullDownRefresh();
			}, 1000)
		},
		// 监听页面拉倒底加载更多数据
		onReachBottom() {
			this.loadMore()
		},
		//监听导航栏点击时间
		onNavigationBarButtonTap(e) {
			if(e.index===1){
				// 显示弹出框
				this.popupShow = true
			}else {
				this.hidePopup()
				// 跳转到好友列表
				uni.navigateTo({
					url: '../friend/friend',
				});
			}
		}
	}
</script>

<style>
	.paper {
		padding: 0 18rpx;
	}

	
</style>
