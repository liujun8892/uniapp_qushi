<template>
	<view>
		<!-- 导航栏 -->
		<new-nav-bar :tabIndex="tabIndex" :tabBar="tabBar" @changeSelected="changeSelected"></new-nav-bar>
		<!-- 滑块 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{'height': screenUseableHeight+'px'}" :current="tabIndex" @change="changeTabCurrent">
				<swiper-item>
					<scroll-view scroll-y :show-scrollbar="false" class="list" @scrolltolower="loadMore('guanzhu')">
						<!-- 数据列表 -->
						<block v-for="(item,index) in newslist" :key="index">
							<common-list :item="item" :index="index" @toggleAttention="toggleAttention"></common-list>
						</block>
						<!-- 子组件加载更多 -->
						<load-more :scrollBottomMsg="scrollBottomMsg"></load-more>
					</scroll-view>
				</swiper-item>
				<swiper-item>
					<scroll-view scroll-y :show-scrollbar="false" class="list" @scrolltolower="loadMore('topic')">
						<!-- 搜索框 -->
						<view class="search">
							<input type="text" placeholder-class="icon iconfont icon-sousuo flex_center" class="ipt_search " placeholder="搜索内容" />
						</view>
						<!-- 轮播图 -->
						<focus :focus_list="focus_list"></focus>
						<!-- 热门分类 -->
						<hot-categories></hot-categories>
						<!-- 最近更新 -->
						<view class="nearly_title">
							最近更新
						</view>
						<nearlyUpdate :update_list="update_list"></nearlyUpdate>
					</scroll-view>

				</swiper-item>
			</swiper>
		</view>

	</view>
</template>

<script>
	// 导入头部导航栏
	import newNavBar from '../../components/news/new-nav-bar.vue'
	// 导入公共样式列表
	import commonList from '../../components/common/commonList/commonList.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	// 导入无数据默认显示组件
	import nothing from '../../components/common/nothing/nothing.vue'
	// 导入轮播图组件
	import focus from '../../components/common/focus/focus.vue'
	// 导入热门分类组件
	import hotCategories from '../../components/news/hot-categories.vue'
	// 导入最近更新组件
	import nearlyUpdate from '../../components/news/nearly_update.vue'
	export default {
		// 挂载组件
		components: {
			newNavBar,
			commonList,
			loadMore,
			nothing,
			focus,
			hotCategories,
			nearlyUpdate
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
				dot_bgc: 'blue',
				dot_current: 'pink',
				tabIndex: 0,
				foucusCurrent: 0,
				tabBar: [{
					title: '关注',
					id: 0
				}, {
					title: '话题',
					id: 1
				}],
				//屏幕可使用高度
				screenUseableHeight: 500,
				scrollBottomMsg: '下拉加载更多',
				newslist: [{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
						username: '三鱼先生',
						usersex: 0, // 0 男 1 女  
						isGuanZhu: true,
						title: '六道快手家常菜，好吃又下饭，家人都喜欢',
						isMedia: true,
						isMovie: true,
						isPicArticle: false,
						mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
						picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
						picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
						address: '深圳  龙岗',
						sharenum: 34,
						commentnum: 54,
						likenum: 35
					}, {
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/7.jpg',
						username: '三鱼小姐',
						usersex: 1, // 0 男 1 女  
						isGuanZhu: true,
						title: '六道快手家常菜，好吃又下饭，家人都喜欢',
						isMedia: true,
						isMovie: false,
						isPicArticle: false,
						mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/7.jpg',
						picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
						picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
						address: '深圳  龙岗',
						sharenum: 34,
						commentnum: 54,
						likenum: 35
					},
					{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
						username: '三鱼先生',
						usersex: 0, // 0 男 1 女  
						isGuanZhu: true,
						title: '六道快手家常菜，好吃又下饭，家人都喜欢',
						isMedia: false,
						isMovie: false,
						isPicArticle: false,
						mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
						picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
						picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
						address: '深圳  龙岗',
						sharenum: 34,
						commentnum: 54,
						likenum: 35
					},
					{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
						username: '三鱼先生',
						usersex: 0, // 0 男 1 女  
						isGuanZhu: true,
						title: '六道快手家常菜，好吃又下饭，家人都喜欢',
						isMedia: false,
						isMovie: false,
						isPicArticle: false,
						mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
						picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
						picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
						address: '深圳  龙岗',
						sharenum: 34,
						commentnum: 54,
						likenum: 35
					},
					{
						userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
						username: '三鱼先生',
						usersex: 0, // 0 男 1 女  
						isGuanZhu: true,
						title: '六道快手家常菜，好吃又下饭，家人都喜欢',
						isMedia: false, // 是媒体资源
						isMovie: false, // 是媒体资源中的电影吗
						isPicArticle: true,
						mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/11.jpg',
						picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
						picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
						address: '深圳  龙岗',
						sharenum: 34,
						commentnum: 54,
						likenum: 35
					}
				],
				// 轮播图图片数据
				focus_list: [{
					img: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/banner1.jpg'
				}, {
					img: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/banner2.jpg'
				}, {
					img: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/banner2.jpg'
				}],
				// 最近更新数据
				update_list: [{
					image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/12.jpeg',
					title: '#淘宝记录簿#',
					topic: '120斤到85斤 我的反转人生',
					newsNum: 545,
					todayNum: 720
				}, {
					image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/11.jpeg',
					title: '#抖音记录美好生活#',
					topic: '地下场订车女孩',
					newsNum: 890,
					todayNum: 540
				}, {
					image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
					title: '#拼多多下沉市场#',
					topic: '农村包围城市',
					newsNum: 990,
					todayNum: 1000
				}]
			}
		},
		methods: {
			// 根据子组件穿过来的索引切换顶部的tab栏
			changeSelected(index) {
				this.tabIndex = index
			},
			// 切换关注状态
			toggleAttention(index, status) {
				this.newslist[index].isGuanZhu = status
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
					if (key === 'guanzhu') {
						let itemObj = {
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
							username: '智子小姐',
							usersex: 1, // 0 男 1 女  
							isGuanZhu: true,
							title: '六道快手家常菜，好吃又下饭，家人都喜欢',
							isMedia: true, // 是媒体资源
							isMovie: true, // 是媒体资源中的电影吗
							isPicArticle: false,
							mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/8.jpg',
							picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
							picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
							address: '深圳  龙岗',
							sharenum: 34,
							commentnum: 54,
							likenum: 35
						}
						for (var i = 0; i < 5; i++) {
							this.newslist.push(itemObj)
						}
			
					} else if (key === 'topic') {
						let topicObj = {
							image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/2.jpeg',
							title: '#任正非得中年心酸#',
							topic: '44岁逆境缝生',
							newsNum: 1110,
							todayNum: 957
						}
						for (var i = 0; i < 5; i++) {
							this.update_list.push(topicObj)
						}
					}
			
				}, 300)
				// 加载完成
				this.scrollBottomMsg = '下拉加载更多'
			},
			// 轮播图的改变
			focusChange(e) {
				this.foucusCurrent = e.detail.current
			}
		}

	}
</script>

<style scoped>
	/* .flex_column {
		padding: 0 15rpx;
	} */

	.search {
		padding: 0 15rpx;
	}

	.ipt_search {
		background-color: #F4F4F4;
		height: 70rpx;
		border-radius: 15rpx;
	}
	
	.nearly_title {
		padding: 0 15rpx;
		font-size: 30rpx;
		margin: 20rpx 0 15rpx 0;
	}

	
</style>
