<template>
	<view>
		<u-section title="招聘信息" font-size="40" :right="false"></u-section>
		<view class="info">
			<!-- 职位名称、岗位职责、公司地点、薪资待遇、联系人、职位描述、职位需求 -->
			<text>职位名称:{{zhaoping.name}}</text>
			<text>岗位职责:{{zhaoping.obligation}}</text>
			<text>公司地点:{{zhaoping.address}}</text>
			<text>薪资待遇:{{zhaoping.salary}}</text>
			<text>联系人:{{zhaoping.contacts}}</text>
			<text>职位描述:{{zhaoping.obligation}}</text>
			<text>职位需求:{{zhaoping.need}}</text>
		</view>
		<u-section title="公司信息" font-size="40" :right="false"></u-section>
		<view class="info">
			<text>公司名称:{{zhaoping.companyName}}</text>
			<text>公司简介:{{zhaoping.companyName}}</text>
		</view>
		<view class="touli">
			<u-button type="primary" @click="touli">投简历</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				zhaoping:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/job/post/'+this.id)
				this.zhaoping=res1.data
				console.log(res1);
			},
			touli(){
				this.$u.post('/prod-api/api/job/deliver',{
					companyId:this.zhaoping.companyId,
					money:this.zhaoping.salary,
					postId:this.zhaoping.professionId,
					postName:this.zhaoping.name
				}).then(res=>{
					console.log(res);
					this.$u.toast('投递成功')
				})
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
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
