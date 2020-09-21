<template>
	<view>
		<!-- tab栏组件 -->
		<index-tabbar-header :tabBars="tabBars" :tabIndex="tabIndex" @toggleTab="changeTabIndex" borderStyle="border: none;"
		 itemWidthStyle="width: 33%;"></index-tabbar-header>


		<!-- 滑块 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{'height': screenUseableHeight+'px'}" :current="tabIndex" @change="changeTabCurrent">
				<block v-for="(val,key) in tabObj">
					<swiper-item>
						<scroll-view scroll-y :show-scrollbar="false" class="list" @scrolltolower="loadMore(key)">
							<template v-if="val.data.length>0">
								<!-- 好友列表组件 -->
								<friend-list :friendList="val.data"></friend-list>
								<!-- 子组件加载更多 -->
								<load-more :scrollBottomMsg="scrollBottomMsg"></load-more>
							</template>
							<template v-else>
								<nothing></nothing>
							</template>
						</scroll-view>
					</swiper-item>
				</block>
			</swiper>
		</view>


		
	</view>
</template>

<script>
	// 引入导航栏组件
	import indexTabbarHeader from '../../components/index/index_tabbar_header.vue'
	// 引入好友列表组件
	import friendList from '../../components/friend/friend_list.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	export default {
		components: {
			indexTabbarHeader,
			friendList,
			loadMore
		},
		onLoad() {
			// 获取设备信息
			uni.getSystemInfo({
				success: (res) => {
					this.screenUseableHeight = res.windowHeight - uni.upx2px(100)
				}
			});
		},
		data() {
			return {
				//屏幕可使用高度
				screenUseableHeight: 500,
				// 下拉加载更多 提示消息
				scrollBottomMsg: '下拉加载更多',
				// tab栏
				tabIndex: 0,
				tabBars: [{
					name: '互关',
					id: 'huguan',
					num: 10
				}, {
					name: '关注',
					id: 'guanzhu',
					num: 8
				}, {
					name: '粉丝',
					id: 'fensi',
					num: 9
				}],
				// 好友列表数据
				tabObj: [{
					id: 'huguan',
					data: [{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/14.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Amazing',
						usersex: 1,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/1.jpg',
						username: 'Supzeol',
						usersex: 1,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
						username: 'Jack',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/9.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}]
				},{
					id: 'huguan',
					data: [{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/14.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Amazing',
						usersex: 1,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/1.jpg',
						username: 'Supzeol',
						usersex: 1,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
						username: 'Jack',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/9.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-xuanze-yixuan'
					}]
				},{
					id: 'huguan',
					data: [{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/14.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-zengjia1'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Amazing',
						usersex: 1,
						iconClass: 'icon iconfont icon-zengjia1'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/1.jpg',
						username: 'Supzeol',
						usersex: 1,
						iconClass: 'icon iconfont icon-zengjia1'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
						username: 'Jack',
						usersex: 0,
						iconClass: 'icon iconfont icon-zengjia1'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-zengjia1'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/9.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-zengjia1'
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: 'icon iconfont icon-zengjia1'
					}]
				}]
			}
		},
		methods: {
			// 改变顶部选项卡索引
			changeTabIndex(index) {
				this.tabIndex = index
			},
			// 改变展示页
			changeTabCurrent(e) {
				this.tabIndex = e.detail.current
			},
			// 加载更多数据
			async loadMore(key) {
				// 如果不是加载更多状态,返回
				if (this.scrollBottomMsg !== '下拉加载更多') return
				// 加载中
				this.scrollBottomMsg = '正在加载数据...'
				// iconClass 
				let iconClass = key===2?'icon iconfont icon-zengjia1':'icon iconfont icon-xuanze-yixuan'
				// 模拟加载数据
				await setTimeout(() => {
					let itemObj ={
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/16.jpg',
						username: 'Supzeol',
						usersex: 0,
						iconClass: iconClass
					}
					for (var i = 0; i < 5; i++) {
						this.tabObj[key].data.push(itemObj)
					}				
				}, 200)
				// 加载完成
				this.scrollBottomMsg = '下拉加载更多'
			},
		},
		onNavigationBarButtonTap(e) {
			// 取消返回
			if (e.index === 0) {
				uni.navigateBack({
					delta: 1
				});
			}
		}
	}
</script>

<style>

</style>
