<template>
	<view>
		<view class="head">
			<u-navbar title="停车场">
				<u-icon @click="totingchejilu" name="list" color="#2979ff" size="44" label="历史停车记录" label-size="33" slot="right" style="margin-right: 10rpx;"></u-icon> 
			</u-navbar> 
		</view>
		<view class="parklist">
			<view class="park" v-for="(item,parklistid) in parklist.slice(0,size)" :key="parklistid" @click="topark_de(parklistid)">
				<!-- 停车场名、空位数量、地址、收费费率、距离 -->
				<h3>{{item.parkName}}</h3>
				<text>空位数量:{{item.vacancy}}</text>
				<text>地址:{{item.address}}</text>
				<text>收费费率:{{item.rates}}元/小时</text>
				<text>距离:{{item.distance}}km</text>
			</view>
			<u-button @click="lookmore" type="success">查看更多</u-button>
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
					url:'tingchejilu'
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
					url:'tingchechang_details?id='+this.parklist[id].id
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
