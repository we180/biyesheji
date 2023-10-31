<template>
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
			<!-- <swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,bannerid) in banner" :key="bannerid">
					<view class="swiper-item">
						<image :src="baseUrl+item.imgUrl" mode="" style="width: 100%;"></image>
					</view>
				</swiper-item>
			</swiper> -->
		</view>
		<view class="type" @click="tozhuanchanglist">
			<swiper :indicator-dots="true" :interval="3000" :duration="1000">
				<swiper-item >
					<view class="swiper-item" v-for="(item,typeid) in type.slice(0,8)" :key="typeid">
						<u-icon :name="baseUrl+item.imgUrl" size="66" label-pos="bottom" :label="item.name"></u-icon>
					</view>
				</swiper-item>
				<swiper-item >
					<view class="swiper-item" v-for="(item,typeid) in type.slice(8,16)" :key="typeid+8">
						<u-icon :name="baseUrl+item.imgUrl" size="66" label-pos="bottom" :label="item.name"></u-icon>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="myzixun">
			<view class="my_icon">
				<u-icon name="account-fill" size="66" label="我的咨询"  color="#2979ff" label-size="34" @click="tozixunlist"></u-icon> 
			</view>
		</view>
		<u-gap></u-gap>
		<u-section title="本月上榜优选律师" font-size="34" sub-title="查看更多" @click="tolvshilist"></u-section>
		<view class="lvshilist" v-for="(item,toplvshiid) in toplvshi" :key="toplvshiid">
			<!-- 头像、名称、从业年限、咨询人数、法律专长、好评率和咨询按钮 -->
			<u-row @click="tolvshi_De(toplvshiid)">
				<u-col span="4">
					<u-image width="100%" height="250rpx" :src="baseUrl+item.avatarUrl"></u-image> 
				</u-col>
				<u-col span="8" style="display: flex;flex-direction: column;" align="top">
					<text>{{item.name}}</text>
					<text>从业年限:{{item.workStartAt}}</text>
					<text>咨询人数:{{item.serviceTimes}}</text>
					<text>法律专长:{{item.legalExpertiseName}}</text>
					<text>好评率:{{item.favorableRate}}</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-button type="success" @click="tozixun">咨询</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				type:[],
				toplvshi:[]
			}
		},
		methods: {
			tozixunlist(){
				uni.navigateTo({
					url:'zixxunlist'
				})
			},
			search(index){
				uni.navigateTo({
					url:'lvshilist?name='+index
				})
			},
			tozhuanchanglist(){
				uni.navigateTo({
					url:'zhuanchanglist'
				})
			},
			tolvshi_De(id){
				uni.navigateTo({
					url:'lvshi_details?id='+this.toplvshi[id].id
				})
			},
			tolvshilist(){
				uni.navigateTo({
					url:'lvshilist'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/lawyer-consultation/ad-banner/list')
				this.banner=res1.data.map(res=>{
					return {
						image:this.baseUrl+res.imgUrl
					}
				})
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/lawyer-consultation/legal-expertise/list')
				this.type=res2.rows.sort((a,b)=>{
					return b.sort-a.sort
				})
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list-top10')
				this.toplvshi=res3.data
				console.log(res3);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	swiper-item{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.swiper-item{
		width: 25%;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.my_icon{
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		height: 100rpx;
		width: 90%;
	}
	.myzixun{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.lvshilist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
