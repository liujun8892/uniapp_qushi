<template>
	<view class="uni-tab-bar">
		<scroll-view id="tab-bar" class="uni-swiper-tab" :style="borderStyle" scroll-x :show-scrollbar="false">
			<view v-for="(tab,index) in tabBars" :key="tab.id" class="swiper-tab-list" :id="tab.id" 
			@tap="changeTabIndex(index)" :style="itemWidthStyle">
				<text :class="{'active':index===tabIndex}">{{tab.name}} {{tab.num?tab.num:''}}</text>
				<view class="tab-bar-line" v-show="index===tabIndex" :class="{'haveNumStyle':tab.num}">
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props: {
			tabBars: Array,
			tabIndex: Number,
			borderStyle: {
				type:String,
				default:""
			},
			itemWidthStyle: {
				type:String,
				default:""
			}
		},
		methods:{
			// 改变顶部选项卡索引
			changeTabIndex(index){
				this.$emit('toggleTab',index)
			}
		}
	}
</script>

<style scoped>
	.uni-swiper-tab {
		border-bottom: 1rpx solid #EEEEEE;
	}
	
	.swiper-tab-list text {
		font-weight: bold;
		color: #b1b1b1;
	}
	
	.swiper-tab-list .active {
		color: #262626;
	}
	
	.tab-bar-line {
		margin: auto;
		border-top: 6rpx solid #FEDE33;
		width: 70rpx;
		border-radius: 6rpx;
	}
	
	.haveNumStyle {
		width: 100rpx;
	}
</style>
