<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true" @click="tohuodong_De_banner"></u-swiper> 
		</view>
		<u-tabs :list="type" :current="current" @change="changetab" style="text-align: center;"></u-tabs>
		<view class="huodonglist" v-for="(item,huodonglistid) in huodonglist" :key="huodonglistid" @click="tohuodong_De(huodonglistid)">
			<!-- 活动图片、活动名称、报名人数、点赞数 -->
			<u-image width="100%" height="270rpx" :src="baseUrl+item.imgUrl"></u-image>
			<h3>{{item.name}}</h3>
			<h4>报名人数:{{item.signupNum}}</h4>
			<h4>点赞数:{{item.likeNum}}</h4>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				banner:[],
				type:[],
				huodonglist:[]
			}
		},
		methods: {
			tohuodong_De(id){
				uni.navigateTo({
					url:'huodong_details?id='+this.huodonglist[id].id
				})
			},
			tohuodong_De_banner(index){
				uni.navigateTo({
					url:'huodong_details?id='+this.banner[index].targetId
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/activity/rotation/list')
				this.banner=res1.rows.map(res=>{
					return {
						image:this.baseUrl+res.advImg,
						targetId:res.targetId
					}
				})
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/activity/category/list')
				this.type=res2.data
				// console.log(res2);
				let res3=await this.$u.get('/prod-api/api/activity/activity/list?categoryId=1')
				this.huodonglist=res3.rows
				console.log(res3);
			},
			changetab(index){
				this.current=index
				this.$u.get('/prod-api/api/activity/activity/list?categoryId='+this.type[index].id).then(res=>{
					this.huodonglist=res.rows
				})
			},
		},
		onLoad() {
			this.getData()
		},
	}
</script>

<style scoped>
	.huodonglist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
