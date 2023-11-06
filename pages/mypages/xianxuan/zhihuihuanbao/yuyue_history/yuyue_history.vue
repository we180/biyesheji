<template>
	<view>
		<!-- 查询已经预约过的回收历史 -->
		<view class="yuyue_list">
			<h2>垃圾种类:有害垃圾</h2>
			<h3>时间:2023年2月1日10:53:27</h3>
			<h3>垃圾重量:20kg</h3>
		</view>
		<view class="yuyue_list">
			<h2>垃圾种类:可回收垃圾</h2>
			<h3>时间:2023年2月3日12:43:37</h3>
			<h3>垃圾重量:44kg</h3>
		</view>
		<view class="yuyue_list">
			<h2>垃圾种类:厨余垃圾</h2>
			<h3>时间:2023年3月21日15:33:47</h3>
			<h3>垃圾重量:56kg</h3>
		</view>
		<view class="yuyue_list">
			<h2>垃圾种类:不可回收垃圾</h2>
			<h3>时间:2023年5月11日16:13:27</h3>
			<h3>垃圾重量:230kg</h3>
		</view>
		<view class="yuyue_list">
			<h2>垃圾种类:有害垃圾</h2>
			<h3>时间:2023年7月17日1:23:27</h3>
			<h3>垃圾重量:22kg</h3>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.yuyue_list{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
