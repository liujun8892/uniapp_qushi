<template>
	<view>
		<uni-nav-bar :fixed="true" :statusBar="true" :border="false">
			<block slot="left">
				<view class="icon iconfont icon-qiandao" >
						
				</view>	
			</block>
			<block>
				<view class="tabMid flex_center">
					<block v-for="(item,index) in tabBar" :key="index">
						<view class="tabMid_item" :class="{'active':tabIndex===item.id}" @tap="toggleSelected(item.id)">
							<text>{{item.title}}</text> 
							<view class="tabMid_item_line" v-show="tabIndex===item.id">							
							</view>
						</view>
					</block>
				</view>
				
			</block>
			<block slot="right">
				<view class="icon iconfont icon-bianji1" @tap="openDeploy">
					
				</view>
			</block>
		</uni-nav-bar>
	</view>
</template>

<script>
	// 导入自定义导航栏组件
	import uniNavBar from '../depoly/uni-nav-bar/uni-nav-bar.vue'
	export default {
		components: {
			uniNavBar
		},
		props: {
			tabBar: Array,
			tabIndex: Number
		},
		data() {
			components: {
				uniNavBar
			}
			return {
				
			}
		},
		methods: {
			// 切换选中按钮
			toggleSelected(index) {
				this.$emit('changeSelected',index) 
			},
			// 发布话题
			openDeploy(){
				uni.navigateTo({
					url: '../depoly/depoly'
				});
			}
		}
	}
</script>

<style scoped>
.icon-qiandao,.icon-bianji1 {
	font-size: 44rpx;
}
.icon-qiandao {
	color: #FF8700;
}
.tabMid_item {
	position: relative;
	text-align: center;
	width: 85rpx;
	color: #959595;
	font-weight: bold;
}
.active {
	color: #282828;
}
.tabMid_item_line {
	position: absolute;
	margin: auto;
	border-top: 6rpx solid #FEDE33;
	width: 65rpx;
	border-radius: 6rpx;
	bottom: 0;
	left: 10rpx;
}
</style>
