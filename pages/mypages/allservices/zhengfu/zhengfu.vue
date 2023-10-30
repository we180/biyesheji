<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true" :interval="3000"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="typelist">
			<swiper :indicator-dots="true" :duration="1000">
				<swiper-item>
					<view class="typelist" v-for="(item,typelistid) in typelist.slice(0,8)" :key="typelistid" @click="tosuqiulist(typelistid)">
						<u-icon :name="baseUrl+item.imgUrl" :label="item.name" label-pos="bottom" size="80" label-size="25"></u-icon>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="typelist" v-for="(item,typelistid) in typelist.slice(8,15)" :key="typelistid" @click="tosuqiulist(typelistid+8)">
						<u-icon :name="baseUrl+item.imgUrl" :label="item.name" label-pos="bottom" size="80" label-size="25"></u-icon>
					</view>
					<view class="typelist" v-for="(item,typelistid) in typelist2" :key="typelistid+'s'" @click="toxinjiansuqiu">
						<u-icon :name="baseUrl+item.imgUrl" :label="item.name" label-pos="bottom" size="80" label-size="25"></u-icon>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<u-section title="我的诉求" font-size="40" :right="false"></u-section>
		<view class="suqiulist">
			<view class="suqiu" v-for="(item,suqiulistid) in suqiulist" :key="suqiulistid">
				<text>{{item.appealCategoryName}}</text>
				<text>{{item.content}}</text>
				<text>{{item.createTime}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				typelist:[],
				suqiulist:[],
				typelist2:[]
			}
		},
		methods: {
			toxinjiansuqiu(){
				uni.navigateTo({
					url:'xinjiansuqiu?other=1'
				})
			},
			tosuqiulist(id){
				uni.navigateTo({
					url:'suqiulist?id='+this.typelist[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/gov-service-hotline/ad-banner/list')
				this.banner=res1.data.map(res=>{
					return{
						image:this.baseUrl+res.imgUrl
					}
				})
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/gov-service-hotline/appeal-category/list')
				this.typelist=res2.rows.slice(0,15)
				this.typelist2=res2.rows.slice(15,16)
				this.typelist.sort(function(a,b){
					return b.sort-a.sort
				})
				// console.log(res2);
				let res3=await this.$u.get('/prod-api/api/gov-service-hotline/appeal/my-list')
				this.suqiulist=res3.rows
				// console.log(res3);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.typelist>*{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	swiper-item{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	swiper-item>*{
		width: 25%;
	}
	.suqiu{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
	}
</style>
