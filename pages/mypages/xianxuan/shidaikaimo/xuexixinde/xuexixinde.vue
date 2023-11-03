<template>
	<view>
		<view class="head">
			<u-navbar title="学习心得">
				<u-icon name="order" color="#2979ff" size="50" label="学习历史" slot="right" style="margin-right: 20rpx;" @click="toxuexi_history"></u-icon> 
			</u-navbar> 
		</view>
		<view class="biji_list">
			<u-section title="学习笔记" font-size="40"></u-section>
			<view class="biji" v-for="(item,bijiid) in 3" :key="bijiid">
				<h3>最美志愿者 弘扬时代先锋</h3>
				<text class="u-line-4">
					2月5日是国际志愿者日，为了弘扬志愿服务精神。綦江区古南街道对24名最美志愿者进行了表彰。
					“虽然上年纪了，但是还是可以在社区发挥余热嘛，做一些力所能及的事情，也希望大家都参与到我们的志愿服务活动中来。”张丽萍老人接过奖状激动地说了自己的获奖感言。
				</text>
			</view>
		</view>
		<view class="ganyan_list">
			<u-section title="学习感言" font-size="40"></u-section>
			<view class="ganyan" v-for="(item,ganyanid) in 3" :key="ganyanid">
				<h3>钢铁意志 人民英雄</h3>
				<text class="u-line-4">
					麦贤得，广东潮汕人，1945年出生于广东省潮州市饶平县汫洲镇一个船民家庭。  1964年3月参加中国人民解放军。1965年8月加入中国共产党。入伍后到广东虎门沙角海军联合学校学习。毕业后，被分配到海军护卫艇第41大队4中队611号护卫艇上，当了一名机电兵。 
				</text>
			</view>
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
			toxuexi_history(){
				uni.navigateTo({
					url:'xuexi_history'
				})
			},
		}
	}
</script>

<style scoped>
	.biji{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
	.ganyan{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
