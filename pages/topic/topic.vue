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
									<!-- 子组件数据列表模板 -->
									<nearly-update :update_list="val" ></nearly-update>
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
	// 导入头部tabbar
	import tabberHeader from '../../components/index/index_tabbar_header.vue'
	// 导入最近更新模板组件
	import nearlyUpdate from '../../components/news/nearly_update.vue'
	// 导入下拉加载更多组件
	import loadMore from '../../components/common/loadMore/load_more.vue'
	// 导入无数据默认显示组件
	import nothing from '../../components/common/nothing/nothing.vue'

	export default {
		components: {
			tabberHeader,
			loadMore,
			nothing,
			nearlyUpdate
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
				screenUseableHeight: 300,
				scrollBottomMsg: '下拉加载更多',
				tabObj: {
					guanzhu: [{
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
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					}],
					tuijian: [{
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
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					}],
					tiyu: [{
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
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					},{
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/10.jpeg',
						title: '#拼多多下沉市场#',
						topic: '农村包围城市',
						newsNum: 990,
						todayNum: 1000
					}],
					hot: [],
					econic: [],
					yule: [],
					junshi: [],
					lishi: [],
					bendi: []
				},
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
						image: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/topicpic/2.jpeg',
						title: '#任正非得中年心酸#',
						topic: '44岁逆境缝生',
						newsNum: 1110,
						todayNum: 957
					}
					this.tabObj[key].push(itemObj)
					this.tabObj[key].push(itemObj)
				}, 200)
				// 加载完成
				this.scrollBottomMsg = '下拉加载更多'
			},
			
			
			
			
			
		}
	}
</script>

<style>

</style>
