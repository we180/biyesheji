<template>
	<view>
		<!-- 岗位名称、公司名称、薪资和投递简历时间 -->
		<view class="toudi_list" v-for="(item,toudilistid) in toudilist" :key="toudilistid">
			<text>岗位名称:{{item.postName}}</text>
			<text>公司名称:{{item.companyName}}</text>
			<text>薪资:{{item.money}}</text>
			<text>投递简历时间:{{item.satrTime}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				toudilist:[]
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/job/deliver/list')
				this.toudilist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.toudi_list{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
