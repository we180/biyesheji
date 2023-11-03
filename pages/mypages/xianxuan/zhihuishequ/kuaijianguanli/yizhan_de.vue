<template>
	<view>
		<view class="yizhaninfo">
			<view class="image">
				<u-image src="../../../../../static/myimgs/myimg_shequ/2.jpg" width="100%" height="400rpx"></u-image>
			</view>
			<view class="yizhantext">
				<h3>菜鸟驿站</h3>
				<text>距离:2.6km</text>
				<text>电话:1145141919</text>
				<text>地址:新日暮里14号</text>
			</view>
		</view>
		<view class="qujianlist">
			<u-section title="全部快件" :right="false" font-size="40"></u-section>
			<u-tabs :list="list" :current="current" @change="changetab" style="text-align: center;"></u-tabs>
			<view class="qujian">
				<view class="image">
					<u-image src="../../../../../static/myimgs/myimg_shequ/KuaiDi.png.png" width="200rpx" height="170rpx"></u-image>
				</view>
				<view class="info">
					<text>取件码:3548-6-54</text>
					<text>顺丰快递:1687412354</text>
					<text>日期:2022/12/8</text>
				</view>
				<view class="info" v-if="current==0">
					<u-button type="primary" @click="qujian">取件</u-button>
				</view>
			</view>
			<u-gap></u-gap>
			<view class="qujian">
				<view class="image">
					<u-image src="../../../../../static/myimgs/myimg_shequ/KuaiDi.png.png" width="200rpx" height="170rpx"></u-image>
				</view>
				<view class="info">
					<text>取件码:3548-6-54</text>
					<text>顺丰快递:1687412354</text>
					<text>日期:2022/12/8</text>
				</view>
				<view class="info" v-if="current==0">
					<u-button type="primary" @click="qujian">取件</u-button>
				</view>
			</view>
			<u-gap></u-gap>
			<view class="qujian">
				<view class="image">
					<u-image src="../../../../../static/myimgs/myimg_shequ/KuaiDi.png.png" width="200rpx" height="170rpx"></u-image>
				</view>
				<view class="info">
					<text>取件码:3548-6-54</text>
					<text>顺丰快递:1687412354</text>
					<text>日期:2022/12/8</text>
				</view>
				<view class="info" v-if="current==0">
					<u-button type="primary" @click="qujian">取件</u-button>
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
			qujian(){
				this.$u.toast('取件成功')
			}
		}
	}
</script>

<style scoped>
.yizhantext{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
	.qujian{
		margin: 10rpx;
		display: flex;
		flex-direction: row;
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
