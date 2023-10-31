<template>
	<view>
		<view class="top">
			<u-navbar title="找车位">
				<u-icon @click="totingchejilu" name="list" color="#2979ff" size="44" label="历史停车记录" label-size="33" slot="right" style="margin-right: 10rpx;"></u-icon> 
			</u-navbar> 
		</view>
		<view class="head">
			<h3 style="text-align: center;">当前地理位置:北京</h3>
		</view>
		<u-gap></u-gap>
		<u-section title="附近的停车场列表" font-size="40" :right="false"></u-section>
		<view class="parklist">
			<view class="park" v-for="(item,parklistid) in parklist" :key="parklistid" @click="topark_de(parklistid)">
				<!-- 停车场名称、地址、总车位数、剩余车位数、支付方式、距离、是否对外开发 -->
				<h3>{{item.parkName}}</h3>
				<text>地址:{{item.address}}</text>
				<text>总车位数:{{item.allPark}}</text>
				<text>剩余车位数:{{item.vacancy}}</text>
				<text>支付方式:{{item.rates}}元/小时</text>
				<text>距离:{{item.distance}}km</text>
				<text>是否对外开放:{{item.open=='Y'?'对外开放':'不对外开放'}}</text>
			</view>
			<!-- <u-button @click="lookmore" type="success">查看更多</u-button> -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				parklist:[],
				size:5
			}
		},
		methods: {
			totingchejilu(){
				uni.navigateTo({
					url:'../tingchechang/tingchejilu'
				})
			},
			lookmore(){
				if(this.parklist.length>this.size){
					this.size=this.size+5
				}else{
					this.$u.toast('没有更多了')
				}
			},
			topark_de(id){
				uni.navigateTo({
					url:'../tingchechang/tingchechang_details?id='+this.parklist[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/lot/list')
				this.parklist=res1.rows.sort((a,b)=>{
					return a.distance-b.distance
				})
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.park{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>