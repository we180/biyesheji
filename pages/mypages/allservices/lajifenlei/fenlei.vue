<template>
	<view>
		<view class="banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,bannerid) in banner.slice(0,1)" :key="bannerid">
					<view class="swiper-item">
						<image :src="baseUrl+item.imgUrl" mode="" style="width: 100%;"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<u-gap></u-gap>
		<view class="type" style="display: flex;flex-direction: row;justify-content: space-around;">
			<u-icon @click="tojieshao(0)" name="checkmark" color="#2979ff" size="66" label="可回收垃圾" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tojieshao(1)" name="trash-fill" color="red" size="66" label="有害垃圾" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tojieshao(2)" name="trash" color="orange" size="66" label="厨余垃圾" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tojieshao(3)" name="grid" color="#aaa" size="66" label="其他垃圾" label-size="33" label-pos="bottom"></u-icon>
		</view>
		<u-tabs :list="type" :current="current" @change="changetab"></u-tabs>
		<view class="remenall">
			<view class="remen" v-for="(item,laji_listid) in laji_list" :key="laji_listid" @click="tolaji_de(laji_listid)">
				<h3>{{item.name}}</h3>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				banner:[],
				type:[],
				laji_list:[]
			}
		},
		methods: {
			tolaji_de(id){
				uni.navigateTo({
					// url:'laji_details?id='+this.laji_list[id].type
					url:'fenleijieshao?id='+this.laji_list[id].type
				})
			},
			changetab(index){
				this.current=index
				this.$u.get('/prod-api/api/garbage-classification/garbage-example/list?type='+this.type[index].id).then(res=>{
					this.laji_list=res.rows
				})
			},
			tojieshao(id){
				if(id==0){
					uni.navigateTo({
						url:'fenleijieshao?id=8'
					})
				}else if(id==1){
					uni.navigateTo({
						url:'fenleijieshao?id=9'
					})
				}else if(id==2){
					uni.navigateTo({
						url:'fenleijieshao?id=10'
					})
				}else if(id==3){
					uni.navigateTo({
						url:'fenleijieshao?id=11'
					})
				}
				
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/garbage-classification/poster/list')
				this.banner=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/garbage-classification/garbage-classification/list')
				this.type=res2.rows
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/garbage-classification/garbage-example/list?type=8')
				this.laji_list=res3.rows
				console.log(res3);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.remen{
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		width: 25%;
		height: 100rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.remenall{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
</style>
