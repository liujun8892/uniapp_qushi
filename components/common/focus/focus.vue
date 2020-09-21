<template>
	<!-- 轮播图 -->
	<swiper :autoplay="true" :interval="3000" :circular="true" :duration="1000" class="slide_focus "
	 :indicator-dots="true" indicator-color="rgba(255,255,255,.3)" indicator-active-color="#ffffff">
		<block v-for="(item,index) in focus_list" :key="index">
			<swiper-item class="focus_item">
				<image :src="item.img" mode="widthFix" lazy-load></image>
			</swiper-item>
		</block>
	</swiper>
</template>

<script>
	export default {
		props: {
			focus_list: Array
		}
	}
</script>

<style scoped>
	.slide_focus {
		padding: 0 15rpx;
		margin-top: 19rpx;
	}
	
	.swiper-item {
		border-radius: 15rpx;
	}
	
	.focus_item {
		border-radius: 20rpx;
	}
	
	.slide_focus image {
		width: 100%;
		height: 340rpx;
	}
	
</style>
