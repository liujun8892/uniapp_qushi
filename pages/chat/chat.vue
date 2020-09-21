<template>
	<view>
		<!-- 滚动swiper -->
		<scroll-view scroll-y :scroll-top="scrollTop" :scroll-with-animation="true" :style="{'height':scrollHeight+ 'px'}" id="scrollView">
			<!-- 聊天数据列表 -->
			<chat-list :chatMsgList="chatMsgList" id="chatList"></chat-list>
			<view class="holder_box"></view>
		</scroll-view>
		

		<!-- 底部的固定信息输入框 -->
		<chat-input @sendMsg="sendMsg"></chat-input>
	</view>
</template>

<script>
	// 导入处理时间的库
	import getTime from '../../common/time.js'
	// 导入底部输入框组件
	import chatInput from '../../components/chat/chat_input.vue'
	// 引入聊天数据列表组件
	import chatList from '../../components/chat/chat_list.vue'
	export default {
		components:{
			chatInput,
			chatList
		},
		data() {
			return {
				// 输入信息
				text: '',
				// 聊天数据列表
				chatMsgList: [],
				// 滚动区域高度
				scrollHeight: 500,
				// 设置顶部滚动高度
				scrollTop:0,
				// chat-list的高度
				chatListHeight: 0
			}
		},
		onLoad() {
			//获取聊天数据列表
			this.getData()
			// 初始化屏幕滚动条高度
			this.initData()
			
		},
		onReady() {
			this.getChatListHeight()
		},
		methods: {
			// 获取滚动区域高度
			initData() {
				// 获取设备信息
				uni.getSystemInfo({
					success: (res) => {
						this.scrollHeight = res.windowHeight - uni.upx2px(100)
					}
				});
			},
			// 
			getChatListHeight() {
			  let uSelQuery =	uni.createSelectorQuery()
			  uSelQuery.select('#scrollView').boundingClientRect()
			  uSelQuery.select('#chatList').boundingClientRect()
			  uSelQuery.exec(res=>{
				  console.log('scrollTop--'+ this.scrollTop);
				  console.log('res---'	+res[1].height);
				 if(res[1].height>this.scrollHeight){
					 this.scrollTop = res[1].height
				 }
			  })
			},
			// 发送消息
			sendMsg(text) {
				this.text = text
				let timeStamp = (new Date().getTime()/1000).toFixed(0)+''
				let formatTime = getTime.gettime.getChatTime(timeStamp, this.chatMsgList[this.chatMsgList.length-1].timeStamp);
				let msgObj = {
					isMe: true,
					isText: true,
					timeStamp: timeStamp,
					formatTime: formatTime,
					friendPic: '',
					sendText: text,
					sendPic: '',
					myPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg'
				}
				this.chatMsgList.push(msgObj)
				this.getChatListHeight()
			},
			getData() {
				// 获取数据
				let arr = [{
					isMe: false,
					isText: true,
					timeStamp: '1589033914',
					friendPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/19.jpg',
					sendText: '终身学习,用好大脑',
					sendPic: '',
					myPic: ''
				}, {
					isMe: true,
					isText: true,
					timeStamp: '1594254735',
					friendPic: '',
					sendText: '空谈误国,实干兴邦;富强,民主,共建人类命运共同体',
					sendPic: '',
					myPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg'
				}, {
					isMe: false,
					isText: false,
					timeStamp: '1594279935',
					friendPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/19.jpg',
					sendText: '',
					sendPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/2.jpg',
					myPic: ''
				}, {
					isMe: true,
					isText: false,
					timeStamp: '1594305135',
					friendPic: '',
					sendText: '',
					sendPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/datapic/6.jpg',
					myPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg'
				}, {
					isMe: true,
					isText: true,
					timeStamp: '1594305235',
					friendPic: '',
					sendText: '下次再聊',
					sendPic: '',
					myPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg'
				},{
					isMe: true,
					isText: true,
					timeStamp: '1594305235',
					friendPic: '',
					sendText: '下次再聊',
					sendPic: '',
					myPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg'
				},{
					isMe: true,
					isText: true,
					timeStamp: '1594305235',
					friendPic: '',
					sendText: '下次再聊',
					sendPic: '',
					myPic: 'https://qushi3.oss-cn-beijing.aliyuncs.com/static/img_mock/userpic/10.jpg'
				}];
				// 处理数据 时间  本条消息和上一条消息比较,如果小于5分钟就不现实消息时间,否则显示并转化时间格式
				// bug 这里必须使用两个循环,先把上一个时间选出来,再循环处理时间数据才可以,不然就会报undefied can't toString() ;猜测可能是异步数据没有获取到,但是就以一个三元表达式获取list
				let timeArr = []
				for (let i = 0; i < arr.length; i++) {
					timeArr.push(i > 0 ? arr[i - 1].timeStamp : 0)
				}
				for (let i = 0; i < timeArr.length; i++) {
					arr[i].formatTime = getTime.gettime.getChatTime(arr[i].timeStamp, timeArr[i]);
				}
				// 赋值
				this.chatMsgList = arr
			}
		}
	}
</script>

<style>
.holder_box {
	height: 150rpx;
}	


</style>
