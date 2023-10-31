<template>
	<view>
		<view class="headimg">
			<u-image width="100%" height="300rpx" :src="baseUrl+headimg"></u-image>
			<text class="u-line-3" style="margin: 10rpx;">{{headtext}}</text>
		</view>
		<view class="rencaizhengce">
			<view class="rencaiimg" v-for="(item,rencaizhengceid) in rencaizhengce" :key="rencaizhengceid" @click="torencai_De(rencaizhengceid)">
				<u-image width="100%" height="250rpx" :src="baseUrl+item.imgUrl" style="border-radius: 20rpx;"></u-image> 
			</view>
		</view>
		<view class="yizhanlist" v-for="(item,yizhanlistid) in yizhanlist" :key="yizhanlistid" >
			<u-row @click="toyizhan_De(yizhanlistid)">
				<u-col span="4">
					<u-image width="100%" height="230rpx" :src="baseUrl+item.coverImgUrl"></u-image> 
				</u-col>
				<u-col span="8">
					<view class="yizhantest">
						<h3>{{item.name}}</h3>
						<text>剩余床位(男):{{item.bedsCountBoy}}</text>
						<text>剩余床位(女):{{item.bedsCountGirl}}</text>
						<text>{{item.address}}</text>
					</view>
				</u-col>
			</u-row>
			<u-collapse>
				<u-collapse-item title="站点介绍">
					{{item.introduce}}
				</u-collapse-item>
			</u-collapse>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				headimg:'',
				headtext:'',
				yizhanlist:[],
				rencaizhengce:[]
			}
		},
		methods: {
			toyizhan_De(id){
				uni.navigateTo({
					url:'yizhan_details?id='+this.yizhanlist[id].id
				})
			},
			torencai_De(id){
				uni.navigateTo({
					url:'rencaizhengce?id='+this.rencaizhengce[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/youth-inn/youth-inn/list')
				this.yizhanlist=res1.rows
				this.headimg=res1.rows[0].coverImgUrl
				this.headtext=res1.rows[0].introduce
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/youth-inn/talent-policy-area/list')
				this.rencaizhengce=res2.data
				console.log(res2);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.rencaizhengce{
		display: flex;
		flex-direction: row;
		
	}
	.rencaiimg{
		width: 33.333%;
		margin: 8rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		overflow: hidden;
	}
	.yizhantest{
		display: flex;
		flex-direction: column;
	}
	.yizhanlist{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
