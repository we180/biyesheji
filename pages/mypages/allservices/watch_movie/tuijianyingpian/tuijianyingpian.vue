<template>
	<view>
		<view class="tuijian" v-for="(item,re_yingpianid) in re_yingpian" :key="re_yingpianid" @click="toyingpian_de(re_yingpianid)">
			<u-image width="100%" height="300rpx" :src="baseUrl+item.cover"></u-image>
			<h2 style="text-align: center;">{{item.name}}</h2>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				re_yingpian:[]
			}
		},
		methods: {
			toyingpian_de(id){
				uni.navigateTo({
					url:'../yingpian_details?id='+this.re_yingpian[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/film/list?recommend=Y')
				this.re_yingpian=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.tuijian{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
