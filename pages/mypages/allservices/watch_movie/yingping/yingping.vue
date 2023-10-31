<template>
	<view>
		<view class="">
			<view class="yingpianlist" v-for="(item,yingpianid) in yingpian" :key="yingpianid" @click="toyingpian_De(yingpianid)">
				<u-image width="100%" height="300rpx" :src="baseUrl+item.cover"></u-image> 
				<h2 class="u-line-2" style="text-align: center;">{{item.name}}</h2>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yingpian:[]
			}
		},
		methods: {
			toyingpian_De(id){
				uni.navigateTo({
					url:'../yingpian_details?id='+this.yingpian[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/film/list')
				this.yingpian=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.yingpianlist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
