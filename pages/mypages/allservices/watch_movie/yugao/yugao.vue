<template>
	<view>
		<view class="head" style="display: flex;flex-direction: row;">
			<u-icon name="map" color="#2979ff" size="60" label="南京" label-size="32"></u-icon>
			<view class="serach" style="width: 80%;">
				<u-search @custom="search" @search="search"></u-search>
			</view>
		</view>
		<!-- 预告片封面、影片名称，点击一个卡片播放预告片 -->
		<view class="yugao_list" v-for="(item,yugaolistid) in yugaolist" :key="yugaolistid">
			<u-image width="100%" height="200rpx" :src="baseUrl+item.cover"></u-image>
			<h2 style="text-align: center;">影片名称:{{item.name}}</h2>
			<video :src="baseUrl+item.video" controls style="width: 100%;"></video>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yugaolist:[]
			}
		},
		methods: {
			search(index){
				this.$u.get('/prod-api/api/movie/film/preview/list?name='+index).then(res=>{
					console.log(res);
					this.yugaolist=res.rows
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/film/preview/list')
				this.yugaolist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.yugao_list{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
