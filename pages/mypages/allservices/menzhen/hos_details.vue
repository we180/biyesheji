<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<view class="text">
			<u-parse :html="hos_details.brief"></u-parse>
		</view>
		<view class="yuyue">
			<u-button type="success" @click="tocard">预约挂号</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id: '',
				banner: [],
				hos_details: ''
			}
		},
		methods: {
			tocard(){
				uni.navigateTo({
					url:'jiuzhen_card'
				})
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/hospital/banner/list?hospitalId=' + this.id)
				this.banner = res1.data.map((res) => {
					return {
						image: this.baseUrl + res.imgUrl
					}
				})
				// console.log(res1);
				let res2 = await this.$u.get('/prod-api/api/hospital/hospital/' + this.id)
				this.hos_details = res2.data
				console.log(res2);
			}
		},
		created() {
			this.getData()
		},
		onLoad(options) {
			this.id = options.id
		}
	}
</script>

<style scoped>
	.text {
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: solid 4rpx pink;
		box-shadow: 8rpx 8rpx 16rpx skyblue;
		background-color: aliceblue;
	}
</style>
