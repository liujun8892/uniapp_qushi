<template>
	<view>
		<!-- 顶部自定义导航栏 -->
		<uni-nav-bar :statusBar="true" left-icon="back" rightText="发布" @clickLeft="back" @clickRight="depoly">
			<view class="flex_center" @tap="changLook">
				<text>{{lookMsg}} </text>
				<view class="icon iconfont icon-xialazhankai">

				</view>
			</view>
		</uni-nav-bar>

		<!-- 文本输入框域 -->
		<view class="uni-textarea">
			<textarea v-model="depolyMsg" placeholder="想说点什么..."  />
			</view>
		
		<!-- 上传图片组件 -->
		<upload-img @changeImg="changeImgList"></upload-img>
		
		<!-- 提示框 -->
		<uni-popup id="popup" ref="popup" :type="type" :animation="false" @change="change" class="animate__animated animate__fadeIn ">
			<view class="popup-content">
				<image src="https://qushi3.oss-cn-beijing.aliyuncs.com/static/common/tanchuan.png" mode="widthFix"></image>
				<view class="">
					1、涉及黄色、政治，广告及骚扰信息
				</view>
				<view class="">
					2、涉及人生攻击
				</view>
				<view class="">
					3、留联系方式，透漏他人隐私
				</view>
				<view class="">
					一禁核实将被封禁，情节严重者永久封禁
				</view>
				<button type="default" @tap="hideDiolog">朕知道了</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	// 导入自定义导航栏
	import uniNavBar from '../../components/depoly/uni-nav-bar/uni-nav-bar.vue'
	// 导入上传图片组件
	import uploadImg from '../../components/common/uploadImg/upload.vue'
	// 导入弹出框组件
	import uniPopup from '../../components/depoly/uni-popup/uni-popup.vue'
	export default {
		// 挂载组件
		components: {
			uniNavBar,
			uploadImg,
			uniPopup
		},
		data() {
			return {
				lookMsg: '所有人可见',
				lookList: [
					'所有人可见',
					'仅自己可见'
				],
				depolyMsg: '',
				imageList:[],
				type: 'center',
				// 对话框
				showPopup: false
			}
		},
		methods: {
			// 返回
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			// 发布
			depoly() {
				console.log('发布');
				this.$refs.popup.open()
			},
			// 更改可见状态
			changLook() {	
				uni.showActionSheet({
					itemList: this.lookList,
					success: (res) => {
						this.lookMsg = this.lookList[res.tapIndex]
					},
				});
			},
			// 更改图片
			changeImgList(imageList) {
				this.imageList = imageList
				console.log(this.imageList);
			},
			/**
			 * popup 状态发生变化触发
			 */
			change(e) {
				//console.log('popup ' + e.type + ' 状态', e.show)
			},
			// 隐藏
			hideDiolog(done) {
				this.$refs.popup.close()
			}
		}
	}
</script>

<style scoped>

	
	.popup-content {
		display: flex;
		flex-direction: column;
		background-color: #FFFFFF;
		padding: 15rpx;
		border-radius: 20rpx;
		color: #181818;
	}
	
	.popup-content  image {
		margin-bottom: 20rpx;
		width: 75%;
		align-self: center;
	}
	
	.popup-content button {
		margin-top: 20rpx;
		width: 100%;
		background-color: #FFE934;
	}


</style>
