<template>
	<view>
		<!-- 停车场名称、地址、距离、是否对外开放，如不对外开放或对外开放、车位信息， -->
		<!-- 如停车费３元／小时，剩余车位、收费参考如每小时３元，最高４０元／天 -->
		<view class="park">
			<h2>{{park.parkName}}</h2>
			<text>地址:{{park.address}}</text>
			<text>距离:{{park.distance}}km</text>
			<text>是否对外开放:{{park.open=='Y'?'对外开放':'不对外开放'}}</text>
			<text>车位总数:{{park.allPark}}</text>
			<text>剩余车位:{{park.vacancy}}</text>
			<text>收费参考:{{park.rates}}元/小时,最高{{park.priceCaps}}元/天</text>
		</view>
	</view>
</template>
<script>
	
	export default {
		data() {
			return {
				id:'',
				park:''
			}
		},
		
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/lot/'+this.id)
				this.park=res1.data
				console.log(res1);
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
	
</script>

<style scoped>
	.park{
		display: flex;
		flex-direction: column;
		border-radius: 20rpx;
		border: 2rpx #999 solid;
		margin: 10rpx;
		padding: 10rpx;
	}
</style>
