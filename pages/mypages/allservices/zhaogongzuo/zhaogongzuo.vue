<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<u-section title="热门职位" font-size="40" :right="false"></u-section>
		<view class="type">
			<view class="all_type">
				<text @click="changetype(0)">java开发工程师</text>
			</view>
			<view class="all_type">
				<text @click="changetype(2)">外教</text>
			</view>
			<view class="all_type">
				<text @click="changetype(6)">前台经理</text>
			</view>
		</view>
		<u-section title="职位列表" font-size="40" :right="false"></u-section>
		<view class="type">
			<view class="all_type" v-for="(item,alltypeid) in alltype" :key="alltypeid" @click="changetype(alltypeid)">
				<text>{{item.professionName}}</text>
			</view>
		</view>
		<u-section title="招聘信息" font-size="40" :right="false"></u-section>
		<view class="zhaoping" v-for="(item,zhaopingid) in zhaoping" :key="zhaopingid" @click="tozhaoping_De(zhaopingid)">
			<!-- 职位名称、岗位职责、公司地点、薪资待遇。 -->
			<text>职位名称:{{item.professionName}}</text>
			<text>岗位职责:{{item.obligation}}</text>
			<text>公司地点:{{item.address}}</text>
			<text>薪资待遇:{{item.salary}}</text>
		</view>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<view class="button">
			<u-button type="success" @click="tougaojilu">投递记录</u-button>
			<u-button type="primary" @click="gerenjianli">个人简历</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				alltype:[],
				zhaoping:[]
			}
		},
		methods: {
			search(index){
				this.$u.get('/prod-api/api/job/post/list?name='+index).then(res=>{
					console.log(res);
					this.zhaoping=res.rows
				})
			},
			tozhaoping_De(id){
				uni.navigateTo({
					url:'zhaoping_details?id='+this.zhaoping[id].id
				})
			},
			changetype(id){
				this.$u.get('/prod-api/api/job/post/list?professionId='+this.alltype[id].id).then(res=>{
					console.log(res);
					this.zhaoping=res.rows
				})
			},
			getzhaoping(){
				this.$u.get('/prod-api/api/job/post/list').then(res=>{
					console.log(res);
					this.zhaoping=res.rows
				})
			},
			tougaojilu(){
				uni.navigateTo({
					url:'toudijilu'
				})
			},
			gerenjianli(){
				uni.navigateTo({
					url:'gerenjianli'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/rotation/list?type=2')
				this.banner=res1.rows.map(res=>{
					return{
						image:this.baseUrl+res.advImg
					}
				})
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/job/profession/list')
				this.alltype=res2.rows
				// console.log(res2);
			}
		},
		onLoad() {
			this.getData()
			this.getzhaoping()
		}
	}
</script>

<style scoped>
	.all_type{
		width: 31.333%;
		margin: 1%;
		padding: 1%;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		height: 86rpx;
	}
	.type{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.all_type{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.zhaoping{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
	.button{
		position: fixed;
		bottom: 100rpx;
		display: flex;
		flex-direction: row;
		width: 100%;
	}
</style>
