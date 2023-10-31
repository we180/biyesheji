<template>
	<view>
		<view class="parkinfo">
			<!-- 停车场名称、地址、距离、是否对外开放，如不对外开放或对外开放、车位信息，
			如停车费３元／小时，剩余车位、收费参考如每小时３元，最高30元／天。 -->
			
			
			<!-- 封面、停车场名称、距离、详细地址、支付方式、收费标准、车位信息（总车位数、剩余车位数）、是否对外开发、车场服务。 -->
			<h3 style="text-align: center;">{{parkinfo.parkName}}</h3>
			<u-image width="100%" height="300rpx" :src="baseUrl+'/prod-api/api'+parkinfo.imgUrl"></u-image> 
			<text>详细地址:{{parkinfo.address}}</text>
			<text>距离:{{parkinfo.distance}}km</text>
			<text>是否对外开放:{{parkinfo.open=='Y'?'对外开放':'不对外开放'}}</text>
			<text>支付方式:{{parkinfo.rates}}元/小时,封顶{{parkinfo.priceCaps}}元</text>
			<text>收费标准:{{parkinfo.rates}}元/小时,封顶{{parkinfo.priceCaps}}元</text>
			<text>总停车位:{{parkinfo.allPark}}</text>
			<text>剩余车位:{{parkinfo.vacancy}}</text>
		</view>
		<u-gap></u-gap>
		<u-section title="车场服务" font-size="36" :right="false"></u-section>
		<u-gap></u-gap>
		<u-button type="success" @click="tojiucuo">信息纠错</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				parkinfo:'',
				id:''
			}
		},
		methods: {
			tojiucuo(){
				uni.navigateTo({
					url:'../zhaochewei/xinxijiucuo'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/lot/'+this.id)
				this.parkinfo=res1.data
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
	.parkinfo{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
