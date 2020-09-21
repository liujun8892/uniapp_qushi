<template>
	<view>
		<!-- 子组件头部的选项卡 -->
		<tabber-header :tabBars="tabBars" :tabIndex="tabIndex" @toggleTab="changeTabIndex"></tabber-header>

		<!-- 滑块 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{'height': screenUseableHeight+'px'}" :current="tabIndex" @change="changeTabCurrent">
				<block v-for="(val,key) in tabObj">
					<swiper-item>
						<scroll-view scroll-y :show-scrollbar="false" class="list" @scrolltolower="loadMore(key)">
							<template v-if="val.length>0">
								<block v-for="(item,index) in val" :key="index">
									<!-- 子组件数据列表模板 -->
									<index-item :item="item" :index="index"></index-item>
								</block>
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
	// 导入首页模板组件
	import indexItem from '../../components/index/index_item.vue'
	// 导入头部tabbar
	import tabberHeader from '../../components/index/index_tabbar_header.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	// 导入无数据默认显示组件
	import nothing from '../../components/common/nothing/nothing.vue'
	export default {
		// 挂载的子组件
		components: {
			indexItem,
			tabberHeader,
			loadMore,
			nothing
		},
		data() {
			return {
				// 顶部选项卡
				tabIndex: 0,
				tabBars: [{
					name: '关注',
					id: 'guanzhu'
				}, {
					name: '推荐',
					id: 'tuijian'
				}, {
					name: '体育',
					id: 'tiyu'
				}, {
					name: '热点',
					id: 'redian'
				}, {
					name: '财经',
					id: 'caijing'
				}, {
					name: '娱乐',
					id: 'yule'
				}, {
					name: '军事',
					id: 'junshi'
				}, {
					name: '历史',
					id: 'lishi'
				}, {
					name: '本地',
					id: 'bendi'
				}],
				//屏幕可使用高度
				screenUseableHeight: 500,
				scrollBottomMsg: '下拉加载更多',
				tabObj: {
					guanzhu: [{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
							username: '卤大师',
							isGuanZhu: false,
							title: '走出去，才发现你和别人差的不是一点半点',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
							playNum: '20w',
							playTime: '2:47',
							userLike: {
								flag: 0, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 570,
								disLikeNum: 2
							},
							commentNum: 21,
							shareNum: 14
						},
						{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg',
							username: '西瓜',
							isGuanZhu: true,
							title: '某国千年一见的美女',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/13.jpg',
							playNum: '110w',
							playTime: '2:47',
							userLike: {
								flag: 1, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 1200,
								disLikeNum: 2
							},
							commentNum: 500,
							shareNum: 14
						},
						{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/6.jpg',
							username: '火星人',
							isGuanZhu: false,
							title: '茫茫宇宙，何处成圣',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/8.jpg',
							playNum: '45w',
							playTime: '3:47',
							userLike: {
								flag: 2, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 1200,
								disLikeNum: 2
							},
							commentNum: 400,
							shareNum: 30
						}
					],
					tuijian: [{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/5.jpg',
							username: '苹果玩家',
							isGuanZhu: false,
							title: 'mackbook pro 2020新品',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/5.jpg',
							playNum: '10w',
							playTime: '6:47',
							userLike: {
								flag: 0, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 580,
								disLikeNum: 3
							},
							commentNum: 24,
							shareNum: 14
						},
						{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/4.jpg',
							username: '草莓',
							isGuanZhu: true,
							title: '中路封神我为王',
							type: 'img', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/4.jpg',
							playNum: '110w',
							playTime: '2:47',
							userLike: {
								flag: 1, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 120,
								disLikeNum: 2
							},
							commentNum: 200,
							shareNum: 14
						}
					],
					tiyu: [{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
							username: 'uzi',
							isGuanZhu: false,
							title: '狂小狗',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/3.jpg',
							playNum: '10w',
							playTime: '6:47',
							userLike: {
								flag: 0, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 580,
								disLikeNum: 3
							},
							commentNum: 24,
							shareNum: 14
						},
						{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/9.jpg',
							username: '乔布斯',
							isGuanZhu: true,
							title: '完美',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/9.jpg',
							playNum: '110w',
							playTime: '2:47',
							userLike: {
								flag: 1, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 120,
								disLikeNum: 2
							},
							commentNum: 200,
							shareNum: 14
						},
						{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/5.jpg',
							username: '巴菲特',
							isGuanZhu: true,
							title: '时间价值',
							type: 'movie', //img 图片 movie 视频
							coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/5.jpg',
							playNum: '110w',
							playTime: '2:47',
							userLike: {
								flag: 1, // 0. 未操作 1. 喜欢 2. 不喜欢
								likeNum: 120,
								disLikeNum: 2
							},
							commentNum: 200,
							shareNum: 14
						}
					],
					hot: [],
					econic: []
				},
				// 内容区域数据
				list: [{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
						username: '卤大师',
						isGuanZhu: false,
						title: '走出去，才发现你和别人差的不是一点半点',
						type: 'movie', //img 图片 movie 视频
						coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
						playNum: '20w',
						playTime: '2:47',
						userLike: {
							flag: 0, // 0. 未操作 1. 喜欢 2. 不喜欢
							likeNum: 570,
							disLikeNum: 2
						},
						commentNum: 21,
						shareNum: 14
					},
					{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg',
						username: '西瓜',
						isGuanZhu: true,
						title: '某国千年一见的美女',
						type: 'movie', //img 图片 movie 视频
						coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/13.jpg',
						playNum: '110w',
						playTime: '2:47',
						userLike: {
							flag: 1, // 0. 未操作 1. 喜欢 2. 不喜欢
							likeNum: 1200,
							disLikeNum: 2
						},
						commentNum: 500,
						shareNum: 14
					},
					{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/6.jpg',
						username: '火星人',
						isGuanZhu: false,
						title: '茫茫宇宙，何处成圣',
						type: 'movie', //img 图片 movie 视频
						coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/8.jpg',
						playNum: '45w',
						playTime: '3:47',
						userLike: {
							flag: 2, // 0. 未操作 1. 喜欢 2. 不喜欢
							likeNum: 1200,
							disLikeNum: 2
						},
						commentNum: 400,
						shareNum: 30
					}
				]
			}
		},
		onLoad() {
			// 获取设备信息
			uni.getSystemInfo({
				success: (res) => {
					this.screenUseableHeight = res.windowHeight - uni.upx2px(100)
				}
			});
		},
		// 搜索框被点击原生事件
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
			    url: '../search/search'
			});
		},
		// 导航栏按钮点击事件
		onNavigationBarButtonTap(e){
			if(e.index===1) {
				uni.navigateTo({
					url: '../depoly/depoly'
				});
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
				// 模拟加载数据
				await setTimeout(() => {
					let itemObj = {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/6.jpg',
						username: '火星人',
						isGuanZhu: false,
						title: '茫茫宇宙，何处成圣',
						type: 'movie', //img 图片 movie 视频
						coverPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/8.jpg',
						playNum: '45w',
						playTime: '3:47',
						userLike: {
							flag: 2, // 0. 未操作 1. 喜欢 2. 不喜欢
							likeNum: 1200,
							disLikeNum: 2
						},
						commentNum: 400,
						shareNum: 30
					}
					this.tabObj[key].push(itemObj)
					this.tabObj[key].push(itemObj)
				}, 200)
				// 加载完成
				this.scrollBottomMsg = '下拉加载更多'
			}
		}
	}
</script>

<style>

</style>
