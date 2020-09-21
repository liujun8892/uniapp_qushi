<template>
	<view>
		<!-- 头部公共组件 -->
		<topic-info :topicInfo="topicInfo"></topic-info>
		<!-- tab栏组件 -->
		<index-tabbar-header :tabBars="tabBars" :tabIndex="tabIndex" @toggleTab="changeTabIndex" borderStyle="border: none;"
		 itemWidthStyle="width: 50%;"></index-tabbar-header>
		<!-- 数据列表 -->
		<view class="dataList">
			<!-- 数据列表 -->
			<block v-for="(item,index) in topicList" :key="index">
				<!-- 判断渲染的是默认的数据列表还是最新的数据列表 -->
				<template v-if="tabIndex === index">
					<block v-for="(item1,index1) in item.data" :key="index1">
						<common-list :item="item1" :index="index1" ></common-list>						
					</block>
					<!-- 子组件加载更多 -->
					<load-more :scrollBottomMsg="item.reachBottomMsg"></load-more>
				</template>
				
			</block>
			
		</view>
	</view>
</template>

<script>
	// 导入话题详情页组件
	import topicInfo from '../../components/topic/topic_info.vue'
	// 引入导航栏组件
	import indexTabbarHeader from '../../components/index/index_tabbar_header.vue'
	// 引入公共数据列表组件
	import commonList from '../../components/common/commonList/commonList.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	export default {
		components: {
			topicInfo,
			indexTabbarHeader,
			commonList,
			loadMore
		},
		data() {
			return {
				// 头部数据
				topicInfo: {
					navImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/13.jpeg',
					titleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/13.jpeg',
					title: '亿往事,敬余生',
					newsNum: 793,
					todayNum: 641,
					topic: '面试官:在电梯里巧遇马云你会做什么？90后女孩的回答当场被录用'
				},
				// tab栏
				tabIndex: 0,
				tabBars: [{
					name: '默认',
					id: 'moren'
				}, {
					name: '最新',
					id: 'zuixin'
				}],
				// 话题数据列表
				topicList: [{
					id: 'moren',
					reachBottomMsg: '下拉加载更多',
					data: [{
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/12.jpg',
							username: '三鱼先生',
							usersex: 1, // 0 男 1 女  
							isGuanZhu: true,
							title: '六道快手家常菜，好吃又下饭，家人都喜欢',
							isMedia: true,
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
					]
				}, {
					id: 'zuixin',
					reachBottomMsg: '下拉加载更多',
					data: [{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/1.jpg',
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/2.jpg',
							username: '三鱼先生',
							usersex: 1, // 0 男 1 女  
							isGuanZhu: true,
							title: '六道快手家常菜，好吃又下饭，家人都喜欢',
							isMedia: true,
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/4.jpg',
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/5.jpg',
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
					]
				}]
			}
		},
		// 监听页面拉倒底加载更多数据
		onReachBottom() {
			this.loadMore()
		},
		// 监听下拉刷新数据
		onPullDownRefresh() {
			setTimeout(()=>{
				// 获取数据
				let newList = [{
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/5.jpg',
							username: '神户牛肉',
							usersex: 0, // 0 男 1 女  
							isGuanZhu: true,
							title: '六道快手家常菜，好吃又下饭，家人都喜欢',
							isMedia: true,
							isMovie: true,
							isPicArticle: false,
							mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/7.jpg',
							picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/28.jpg',
							picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
							address: '深圳  龙岗',
							sharenum: 34,
							commentnum: 54,
							likenum: 35
						}, {
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/6.jpg',
							username: '黄渤',
							usersex: 1, // 0 男 1 女  
							isGuanZhu: true,
							title: '六道快手家常菜，好吃又下饭，家人都喜欢',
							isMedia: true,
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/3.jpg',
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/4.jpg',
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
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/5.jpg',
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
					]
				// 刷新数据
				this.topicList[this.tabIndex].data = newList
				uni.stopPullDownRefresh();
			},1000)
			
			
		},
		methods: {
			// 切换tab栏索引
			// 改变顶部选项卡索引
			changeTabIndex(index) {
				this.tabIndex = index
			},
			// 加载更多数据
			async loadMore() {
				// 如果不是加载更多状态,返回
				if (this.topicList[this.tabIndex].reachBottomMsg !== '下拉加载更多') return
				// 加载中
				this.topicList[this.tabIndex].reachBottomMsg = '正在加载数据...'
				// 模拟加载数据
				await setTimeout(() => {					
						let itemObj = {
							userpic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/7.jpg',
							username: '马云',
							usersex: 0, // 0 男 1 女  
							isGuanZhu: true,
							title: '六道快手家常菜，好吃又下饭，家人都喜欢',
							isMedia: true, // 是媒体资源
							isMovie: true, // 是媒体资源中的电影吗
							isPicArticle: false,
							mediaPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/7.jpg',
							picArticleImg: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/6.jpg',
							picArticleTitle: '从男人的角度告诉你，为什么他对你有好感却不追呢',
							address: '深圳  龙岗',
							sharenum: 34,
							commentnum: 54,
							likenum: 35
						}
						for (var i = 0; i < 5; i++) {
							this.topicList[this.tabIndex].data.push(itemObj)
						}		
				}, 300)
				// 加载完成
				this.topicList[this.tabIndex].reachBottomMsg = '下拉加载更多'
			},
		}
	}
</script>

<style scoped>

</style>
