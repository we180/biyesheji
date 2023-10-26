<template>
	<view>
		<u-gap></u-gap>
		<u-section title="所有可预约挂号科室" :right="false" fontSize="40"></u-section>
		<view class="typeall">
			<view class="typelist" v-for="(item,keshi_typeid) in keshi_type" :key="keshi_typeid" @click="toguahao(keshi_typeid)">
				<u-section :title="'科室'+(keshi_typeid+1)" fontSize="35"></u-section>
				<h2>{{item.categoryName}}</h2>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keshi_type:[]
			}
		},
		methods: {
			toguahao(id){
				uni.navigateTo({
					url:'/pages/mypages/allservices/menzhen/guahao?id='+this.keshi_type[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/hospital/category/list')
				this.keshi_type=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.typelist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: solid 4rpx pink;
		box-shadow: 8rpx 8rpx 16rpx skyblue;
		background-color: aliceblue;
		height:140rpx;
		display: flex;
		flex-direction: column;
	}
</style>
