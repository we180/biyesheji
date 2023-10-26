<template>
	<view>
		<view class="search">
			<u-search></u-search>
		</view>
		<u-gap></u-gap>
		<u-section title="全市知名医院" :right="false" fontSize="40"></u-section>
		<view class="recommend">
			<view class="hos_list" v-for="(item,hospital_listid) in hospital_list" :key="hospital_listid" @click="todetails(hospital_listid)">
				<view class="hosimg">
					<image :src="baseUrl+item.imgUrl" mode=""></image>
				</view>
				<view class="hostext">
					<span>{{item.hospitalName}}</span>
					<view class="rate">
						<span>星级:</span><u-rate :current="item.level" :disabled="true"></u-rate>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				hospital_list:[]
			}
		},
		methods: {
			todetails(id){
				uni.navigateTo({
					url:'/pages/mypages/allservices/menzhen/hos_details?id='+this.hospital_list[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/hospital/hospital/list')
				this.hospital_list=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.hosimg image{
		width: 220rpx;
		height: 220rpx;
	}
	.hos_list{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: solid 4rpx pink;
		box-shadow: 8rpx 8rpx 16rpx skyblue;
		background-color: aliceblue;
		display: flex;
		flex-direction: row;
	}
	.hostext{
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		margin-left: 30rpx;
	}
</style>
