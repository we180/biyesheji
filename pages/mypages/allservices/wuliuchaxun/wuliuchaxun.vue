<template>
	<view>
		<view class="search" @click="tosearch">
			<u-search></u-search>
		</view>
		<u-gap></u-gap>
		<view class="banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,bannerid) in banner" :key="bannerid">
					<view class="swiper-item">
						<u-image width="100%" height="300rpx" :src="baseUrl+item.imgUrl" style="width: 100%;"></u-image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<u-gap></u-gap>
		<u-section title="物流公司推荐" font-size="38" :right="false"></u-section>
		<view class="typeall">
			<view class="type" v-for="(item,wuliutuijianid) in wuliutuijian.slice(0,12)" :key="wuliutuijianid" @click="togongsi_de(wuliutuijianid)">
				<u-icon :name="baseUrl+item.imgUrl" size="66" label-pos="bottom" :label="item.name" label-size="24"></u-icon>
			</view>
		</view>
		<u-gap></u-gap>
		<u-section title="其他物流公司" font-size="38" :right="false"></u-section>
		<view class="gongsi_all" v-for="(item,wuliutuijianid) in wuliutuijian" :key="wuliutuijianid" @click="togongsi_de(wuliutuijianid)">
			<h3>{{item.name}}</h3>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				wuliutuijian:[]
			}
		},
		methods: {
			tosearch(){
				uni.navigateTo({
					url:'yundansousuo'
				})
			},
			togongsi_de(id){
				uni.navigateTo({
					url:'gongsi_details?id='+this.wuliutuijian[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/logistics-inquiry/ad-banner/list')
				this.banner=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/logistics-inquiry/logistics_company/list')
				this.wuliutuijian=res2.data
				console.log(res2);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.typeall{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.type{
		width: 25%;
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 20rpx;
	}
	.gongsi_all{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
