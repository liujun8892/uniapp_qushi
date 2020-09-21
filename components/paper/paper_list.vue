<template>
	<view>
		<block v-for="(item,index) in paparList" :key="index">
			<view class="paper_list flex animate__animated animate__zoomIn animate__fast" @tap="openDetail">
				<image :src="item.userpic" mode="widthFix" lazy-load=""></image>
				<view class="paer_content">
					<view class="flex_mBetween_asideCenter info">
						<view class="username">
							{{item.username}}
						</view>
						<view class="">
							{{item.time}}
						</view>
					</view>
					<view class="flex_mBetween_asideCenter content">
						<view>
							{{item.content}}
						</view>
						<template v-if="item.contentNum>0">
							<uni-badge class="uni-badge-left-margin" :text="item.contentNum" type="error" size="small" />
						</template>
					</view>
				</view>
			</view>
		</block>
	</view>

</template>

<script>
	// 导入角标组件
	import uniBadge from '../common/uni-badge.vue'
	export default {
		components: {
			uniBadge
		},
		props: {
			paparList: Array
		},
		methods:{
			openDetail(){
				uni.navigateTo({
					url: '../../pages/chat/chat'
				});
			}
		}
	}
</script>

<style scoped>
	.paper_list {
		padding: 10rpx 0 25rpx 0;
		border-bottom: 1rpx solid #ECECEC;
	}

	.paper_list image {
		margin-right: 18rpx;
		width: 100rpx;
		height: 100rpx;
		border-radius: 50%;
	}

	.paper_list>view {
		flex: 1;
	}

	.info .username {
		font-size: 35rpx;
	}

	.info view:nth-child(2) {
		color: #C1C1C1;
	}

	.content view {
		color: #959595;
	}
</style>
