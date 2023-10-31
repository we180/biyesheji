<template>
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<!-- 活动标题、承办单位、活动开始时间、人员要求和报名按钮 -->
		<view class="huodong" v-for="(item,huodongid) in huodong" :key="huodongid">
			<view class="info" @click="tohuodong_De(huodongid)">
				<h3 style="text-align: center;">{{item.title}}</h3>
				<text>承办单位:{{item.undertaker}}</text>
				<text>活动开始时间:{{item.startAt}}</text>
				<text>人员要求:{{item.requireText}}</text>
			</view>
			<u-button type="success" @click="baoming(huodongid)" style="width: 90%;">报名</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				huodong:[]
			}
		},
		methods: {
			baoming(id){
				// this.$u.post('/prod-api/api/volunteer-service/register',{
				// 	activityId:this.huodong[id].id,
				// 	newState:true
				// }).then(res=>{
				// 	this.$u.toast('报名成功')
				// })
				this.$u.toast('报名成功')
			},
			tohuodong_De(id){
				uni.navigateTo({
					url:'huodong_details?id='+this.huodong[id].id
				})
			},
			search(){
				this.getData()
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/volunteer-service/activity/list')
				this.huodong=res1.rows
				// console.log(res1);
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.huodong{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.info{
		display: flex;
		flex-direction: column;
	}
</style>
