<template>
	<view>
		<!-- 标题、诉求内容、图片、承办单位、提交时间、反馈处理状态和处理结果。 -->
		<view class="suqiuinfo">
			<h2>{{suqiuinfo.title}}</h2>
			<text>{{suqiuinfo.content}}</text>
			<u-image width="100%" height="300rpx" :src="baseUrl+suqiuinfo.imgUrl" v-if="suqiuinfo.imgUrl!==null"></u-image>
			<text>承办单位:{{suqiuinfo.undertaker}}</text>
			<text>提交时间:{{suqiuinfo.createTime}}</text>
			<text>反馈处理状态:{{suqiuinfo.state==0?'未处理':'已处理'}}</text>
			<text v-if="suqiuinfo.state==1">处理结果:{{suqiuinfo.detailResult}}</text>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				suqiuinfo:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/gov-service-hotline/appeal/'+this.id)
				this.suqiuinfo=res1.data
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.suqiuinfo{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
		display: flex;
		flex-direction: column;
	}
</style>
