<template>
	<view>
		<view class="banner u-m-20">
			<u-swiper :list="banner"></u-swiper>
		</view>
		<view class="yizhaninfo">
			<u-section title="周围商铺" font-size="40"></u-section>
			<u-gap></u-gap>
			<view class="yizhan" @click="toshangpu">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/2.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>大东方百货</h3>
							<text>距离:2.6km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里14号</text>
						</view>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/1.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>大润发</h3>
							<text>距离:4.1km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里214号</text>
						</view>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/3.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>沙县小吃</h3>
							<text>距离:4.1km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里614号</text>
						</view>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/4.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>群花馆</h3>
							<text>距离:4.1km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里154号</text>
						</view>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/5.png" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>中庸工艺馆</h3>
							<text>距离:4.1km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里24号</text>
						</view>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/6.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>沉溺海豚亭</h3>
							<text>距离:4.1km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里134号</text>
						</view>
					</u-col>
				</u-row>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner: [
					"../../../../../static/myimgs/myimg_shequ/u=2081009638,1317666904&fm=26&fmt=auto&gp=0.jpg",
					"../../../../../static/myimgs/myimg_shequ/u=2163698466,3692809484&fm=26&fmt=auto&gp=0.jpg"
				],
			}
		},
		methods: {
			toshangpu(){
				uni.navigateTo({
					url:'tuiguang_de'
				})
			},
		}
	}
</script>

<style scoped>
	.yizhantext {
		display: flex;
		flex-direction: column;
	}
</style>
