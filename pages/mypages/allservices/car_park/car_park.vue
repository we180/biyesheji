<template>
	<view>
		<view class="head">
			<u-navbar back-text="返回" title="停哪儿">
				<u-icon name="order" size="42" label="停车记录" slot="right" style="margin-right: 20rpx;" @click="topark_list"></u-icon> 
			</u-navbar>
		</view>
		<!-- 停车场名、空位数量、地址、收费价格、距离 -->
		<view class="parklist" v-for="(item,parklistid) in parklist" :key="parklistid" @click="topark_De(parklistid)">
			<h2>{{item.parkName}}</h2>
			<text>空位数量:{{item.vacancy}}</text>
			<text>地址:{{item.address}}</text>
			<text>收费价格:{{item.rates}}元/小时</text>
			<text>距离:{{item.distance}}km</text>
		</view>
		<view class="button">
			<u-button type="primary" @click="lookmore">查看更多</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				parklist:[],
				total:0,
				pageNum:1
			}
		},
		methods: {
			topark_list(){
				uni.navigateTo({
					url:'park_list'
				})
			},
			topark_De(id){
				uni.navigateTo({
					url:'park_details?id='+this.parklist[id].id
				})
			},
			lookmore(){
				if(this.parklist.length<this.total){
					this.pageNum++
					this.getData()
				}else{
					this.$u.toast('没有更多了')
				}
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/lot/list?pageNum='+this.pageNum+'&pageSize=5')
				this.total=res1.total
				res1.rows.forEach(res=>{
					this.parklist.push(res)
				})
				console.log(res1);
				this.parklist.sort(function(a,b){
					return a.distance-b.distance
				})
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.parklist{
		display: flex;
		flex-direction: column;
		border-radius: 20rpx;
		border: 2rpx #999 solid;
		margin: 10rpx;
		padding: 10rpx;
	}
</style>
