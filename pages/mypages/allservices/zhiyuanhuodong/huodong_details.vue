<template>
	<view>
		<!-- 活动名称、活动简介、活动开始时间、人员要求、承办单位和工作内容。 -->
		<view class="info">
			<h3>{{huodong.title}}</h3>
			<text>活动简介:{{huodong.detail==null?'无':huodong.detail}}</text>
			<text>活动开始时间:{{huodong.startAt}}</text>
			<text>人员要求:{{huodong.requireText}}</text>
			<text>承办单位:{{huodong.undertaker}}</text>
			<!-- <text>工作内容:{{huodong.}}</text> -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				huodong:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/volunteer-service/activity/'+this.id)
				this.huodong=res1.data
				console.log(res1);
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
