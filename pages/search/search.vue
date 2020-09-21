<template>
	<view>		
			<template v-if="searchResultList.length>0">		
					<!-- 子组件数据列表模板 -->
					<index-item :item="item" :index="index" v-for="(item,index) in searchResultList" :key="index"></index-item>
				<!-- 子组件加载更多 -->
				<load-more :scrollBottomMsg="scrollBottomMsg"></load-more>
			</template>
			<template v-else-if="isSearch && searchResultList.length<1">
				<nothing></nothing>
			</template>
	</view>
</template>

<script>
	// 导入首页模板组件
	import indexItem from '../../components/index/index_item.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	// 导入无数据默认显示组件
	import nothing from '../../components/common/nothing/nothing.vue'
	
	export default {
		// 挂载的子组件
		components: {
			indexItem,
			loadMore,
			nothing
		},
		data() {
			return {
				// 判断是否输入
				isSearch: false,
				searchText: '',
				scrollBottomMsg: '下拉加载更多',
				searchResultList: []
			}
		},
		// 导航栏按钮点击事件
		onNavigationBarButtonTap(e){
			if(e.index===0) {
				uni.navigateBack({
					 delta: 1
				})
			}
		},
		// 输入事件
		onNavigationBarSearchInputChanged(e) {
			this.searchText = e.text
		},
		// 确认搜索事件
		onNavigationBarSearchInputConfirmed(e) {
			// 调用搜索方法
			this.search()
		},
		// 触底加载更多
		onReachBottom() {
			this.loadMore()
		},
		// 上啦刷新
		onPullDownRefresh() {
			this.search('refresh')
			uni.stopPullDownRefresh();
		},
		methods: {
			// 搜索方法
			search(type) {
				if(this.searchText.trim().length>0){
					this.getData(this.searchText,type)
				}
			},
			// 获取数据
			getData(params,type) {
				// 开始加载数据
				if(type!=='refresh'){
					uni.showLoading()
				}	
				setTimeout(()=>{
					let searchList = [{
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
						this.searchResultList = searchList
						// 结束加载
						if(type!=='refresh'){
							uni.hideLoading()
						}						
				},1000)
							
			} 
			,
			// 加载更多数据
			async loadMore() {
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
					for (var i = 0; i < 5; i++) {
						this.searchResultList.push(itemObj)
					}		
				}, 400)
				// 加载完成
				this.scrollBottomMsg = '下拉加载更多'
			},
			
			
		}
	}
</script>

<style>

</style>
