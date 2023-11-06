<template>
	<view>
		<view class="info">
			<view class="image">
				<u-image src="../../../../../static/myimgs/myimg_shequ/u=2163698466,3692809484&fm=26&fmt=auto&gp=0.jpg"
					width="100%" height="360rpx"></u-image>
			</view>
			<u-gap></u-gap>
			<view class="text">
				<text>专业回收电子元器件，集成电路，手机IC，二三极管，电解电容，胆电容，，字库，晶振，我们高价回收手机配件，手机屏，液晶屏，液晶总成，手机喇叭，手机尾插，手机连接器，FLash系列闪存，内存，单片机，模块,显卡，网卡，芯片，家电IC、电脑IC、通讯IC、电源IC、数码IC、安防IC、军工IC,K9F系列、南北桥、手机IC、电脑周边IC、电视机IC、ATMEL/PIC系列单片机、SAA系列、XC系列、RT系列、TDA系列、TA系列，手机主控IC，内存卡、字库、蓝牙芯片,功放IC、电解电容、钽电容、贴片电容、晶振、变压器、LED发光管、继电器...电脑配件.手机配件）等一切电子料等。</text>
			</view>
		</view>
		<u-gap></u-gap>
		<view class="comment">
			<u-section title="评论" :right="false" font-size="40"></u-section>
			<u-input type="textarea" border="border" style="margin: 20rpx;" v-model="content"></u-input>
			<u-button type="success" style="margin: 20rpx;" @click="pinglun">发表评论</u-button>
			<u-gap></u-gap>
			<u-section title="评论列表" :right="false" font-size="40"></u-section>
			<view class="commentlist" style="display: flex;flex-direction: column-reverse;">
				<view class="comment_list" v-for="(item,index) in commentlist" :key="index">
					<text>{{item}}</text>
					<text>2022/12/8</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content: '',
				commentlist: [
					"生活不错爱来自乌尔达哈",
					"错的不是我是这个世界！"
				],
			}
		},
		methods: {
			pinglun(){
				this.commentlist.push(this.content)
				this.content=''
				this.$u.toast('评论成功')
			},
		}
	}
</script>

<style scoped>
	.comment_list {
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
	.text{
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
</style>
