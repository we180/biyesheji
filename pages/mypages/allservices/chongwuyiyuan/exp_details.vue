<template>
	<!-- 页面显示医生头像、医生姓名、医生职称、执业编号、去提问按钮、咨询描述、图片和医生回复。点击去提问按钮跳转至问诊页面。 -->
	<view>
		<view class="docinfo">
			<view class="docimg">
				<image :src="baseUrl+item.doctor.avatar" mode=""></image>
		
			</view>
			<h3 style="text-align: center;">{{item.doctor.name}}</h3>
			<view class="doctext">
		
				<text>医生职称:{{item.doctor.jobName}}</text>
				<text>执业编号:{{item.doctor.practiceNo}}</text>
				<text>咨询描述:{{item.question}}</text>
				<image :src="baseUrl+'/prod-api'+item.imageUrls" mode=""></image>
			</view>
		</view>
		<h3 style="text-align: center;">医生回复</h3>
		<view class="wenda">
			<view class="wendalist" v-for="(item,huifuid) in huifu" :key="huifuid">
				<h4>用户ID:{{item.fromId}}</h4>
				<text>{{item.content}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				item:{},
				huifu:[],
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/pet-hospital/inquiry-message/list?inquiryId='+this.item.id)
				this.huifu=res1.rows
				console.log(res1);
			}
		},
		onLoad(options) {
			this.item=JSON.parse(options.item)
			this.getData()
		}
	}
</script>

<style scoped>
	.doctext {
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF solid 2rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
	}
	
	.docimg image {
		width: 100%;
	}
	.wendalist {
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF solid 2rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
	}
</style>
