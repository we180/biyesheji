<template>
<!-- 	上方展示公益详情，包括信息项：项目图片、项目名称、已募善款、筹款目标、项目备案号、参与人数、捐款进度、项目时间
	下方展示项目介绍详细信息，包括文章和对应图片，右侧滚动显示捐助记录
	页面底部显示项目预算清单，展示该项目各笔捐款数额去向与使用细则。 -->
	<view>
		<view class="top">
			<view class="img">
				<image :src="baseUrl+img" mode=""></image>
			</view>
			<view class="text">
				<h3>项目名称:{{name}}</h3>
				<text>已募善款:{{donateCount}}</text>
				<text>筹款目标:{{moneyTotal}}</text>
				<!-- <text>项目备案号</text> -->
				<!-- <text>参与人数{{}}</text> -->
				<!-- <text>捐款进度{{}}</text> -->
				<text>项目时间:{{createTime}}</text>
			</view>
		</view>
		<view class="mid">
			<swiper :indicator-dots="true" :interval="3000" :duration="1000">
				<swiper-item>
					<view class="swiper-item">
						项目列表
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<view class="juanzenglist" v-for="(item,juanzenglistid) in juanzenglist" :key="juanzenglistid">
							<text>捐赠人:{{item.userName}}</text>
							<text>捐赠金额:{{item.donateMoney}}</text>
						</view>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="bottom">
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				name:'',
				img:'',
				moneyTotal:'',
				donateCount:'',
				createTime:'',
				
				juanzenglist:[]
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/public-welfare/donate-record/list?activityId='+this.id)
				this.juanzenglist=res1.rows
				console.log(res1);
			}
		},
		onLoad(options) {
			this.id=options.id
			this.name=options.name
			this.img=options.img
			this.moneyTotal=options.moneyTotal
			this.donateCount=options.donateCount
			this.createTime=options.createTime
			this.getData()
		}
	}
</script>

<style scoped>
	.text{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border: #A0CFFF 2rpx solid;
	}
	.img image{
		width: 100%;
	}
	.juanzenglist{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border: #A0CFFF 2rpx solid;
	}
	swiper{
		height: 50vh;
	}
</style>
