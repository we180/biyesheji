<template>
	<view>
		<!-- 上方显示累计加油量、累计加油金额，中部显示已行驶里程， -->
		<view class="info">
			<h3>累计加油量:{{info[0].gasFilling}}L</h3>
			<h3>累计加油金额:{{info[0].amount}}元</h3>
		</view>
		<view class="info">
			<h3>已行驶里程:{{info[0].travelDistance}}km</h3>
		</view>
		<u-gap></u-gap>
		<!-- 下方以列表形式显示加油记录，底部显示“添加机油记录”按钮，点击此按钮进入添加加油记录页面。 -->
		<u-section title="加油记录" font-size="40" :right="false"></u-section>
		<view class="jiayoujilu">
			<view class="info" style="display: flex;flex-direction: column;">
				<text>加油日期:2022年2月2日</text>
				<text>加油量:10L</text>
				<text>累计加油金额:60元</text>
			</view>
			<view class="info" style="display: flex;flex-direction: column;">
				<text>加油日期:2022年2月5日</text>
				<text>加油量:20L</text>
				<text>累计加油金额:120元</text>
			</view>
			<view class="info" style="display: flex;flex-direction: column;">
				<text>加油日期:2022年2月24日</text>
				<text>加油量:30L</text>
				<text>累计加油金额:180元</text>
			</view>
		</view>
		<view class="button">
			<u-button type="success" @click="addjilu">添加加油记录</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info:[]
			}
		},
		methods: {
			addjilu(){
				uni.navigateTo({
					url:'addjilu'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/car/consumption')
				this.info=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.info{
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		margin: 10rpx;
	}
	.button{
		position: fixed;
		bottom: 5rpx;
		padding: 10rpx;
		width: 100%;
	}
</style>
