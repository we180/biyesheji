<template>
	<view>
		<view class="head">
			<u-navbar title="快件管理">
				<u-icon slot="right" class="u-m-r-20" name="scan" size="50"></u-icon>
			</u-navbar> 
		</view>
		<view class="yizhaninfo">
			<u-section title="快递点" font-size="40"></u-section>
			<u-gap></u-gap>
			<view class="yizhan" @click="toyizhande">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_shequ/2.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>菜鸟驿站</h3>
							<text>距离:2.6km</text>
							<text>电话:1145141919</text>
							<text>地址:新日暮里14号</text>
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
							<h3>小兵驿站</h3>
							<text>距离:4.1km</text>
							<text>电话:3212241919</text>
							<text>地址:新日暮里114号</text>
						</view>
					</u-col>
				</u-row>
			</view>
		</view>
		<u-gap></u-gap>
		<view class="qujianlist">
			<u-section title="全部快件" :right="false" font-size="40"></u-section>
			<u-tabs :list="list" :current="current" @change="changetab" style="text-align: center;"></u-tabs>
			<view class="qujian">
				<view class="image">
					<u-image src="../../../../../static/myimgs/myimg_shequ/KuaiDi.png.png" width="200rpx" height="170rpx"></u-image>
				</view>
				<view class="info">
					<text>取件码:3348-6-54</text>
					<text>顺丰快递:1666412354</text>
					<text>日期:2022/12/8</text>
				</view>
				<view class="info" style="margin-left: 4%;" v-if="current==0">
					<u-button type="primary" @click="toyizhande">取件</u-button>
				</view>
			</view>
			<u-gap></u-gap>
			<view class="qujian">
				<view class="image">
					<u-image src="../../../../../static/myimgs/myimg_shequ/KuaiDi.png.png" width="200rpx" height="170rpx"></u-image>
				</view>
				<view class="info">
					<text>取件码:4248-6-23</text>
					<text>顺丰快递:2323612354</text>
					<text>日期:2022/12/8</text>
				</view>
				<view class="info" style="margin-left: 4%;" v-if="current==0">
					<u-button type="primary" @click="toyizhande">取件</u-button>
				</view>
			</view>
			<u-gap></u-gap>
			<view class="qujian">
				<view class="image">
					<u-image src="../../../../../static/myimgs/myimg_shequ/KuaiDi.png.png" width="200rpx" height="170rpx"></u-image>
				</view>
				<view class="info">
					<text>取件码:6548-3-44</text>
					<text>顺丰快递:1282322354</text>
					<text>日期:2022/12/8</text>
				</view>
				<view class="info" style="margin-left: 4%;" v-if="current==0">
					<u-button type="primary" @click="toyizhande">取件</u-button>
				</view>
			</view>
			<u-gap></u-gap>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				list:[
					{
						name:'未取件'
					},
					{
						name:'已取件'
					}
				]
			}
		},
		methods: {
			changetab(index){
				this.current=index
			},
			toyizhande(){
				uni.navigateTo({
					url:'yizhan_de'
				})
			},
		}
	}
</script>

<style scoped>
	.yizhantext{
		display: flex;
		flex-direction: column;
	}
	.qujian{
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
	.info{
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: 10rpx;
	}
	.info>*{
		margin: 6rpx;
	}
</style>
