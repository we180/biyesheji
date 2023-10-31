<template>
	<view>
		<view class="head" style="display: flex;flex-direction: row;">
			<u-icon name="map" color="#2979ff" size="60" label="南京" label-size="32"></u-icon>
			<view class="serach" style="width: 80%;">
				<u-search @custom="search" @search="search"></u-search>
			</view>
		</view>
		<!-- 包括：封面、影院名称、地址、分数（最高5分，用5颗五角星标识） -->
		<view class="yingyuanlist" v-for="(item,yingyuanlistid) in yingyuanlist" :key="yingyuanlistid" @click="toyingyuan_de(yingyuanlistid)">
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="200rpx" :src="baseUrl+item.cover"></u-image> 
				</u-col>
				<u-col span="8">
					<view class="yingyuantext" style="display: flex;flex-direction: column;">
						<h3>{{item.name}}</h3>
						<text>地址:{{item.address}}</text>
						<u-rate :current="5" :disabled="true"></u-rate> 
					</view>
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yingyuanlist:[]
			}
		},
		methods: {
			search(index){
				this.$u.get('/prod-api/api/movie/theatre/list?name='+index).then(res=>{
					this.yingyuanlist=res.rows
				})
			},
			toyingyuan_de(id){
				uni.navigateTo({
					url:'yingyuan_details?id='+this.yingyuanlist[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/theatre/list')
				this.yingyuanlist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.yingyuanlist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
