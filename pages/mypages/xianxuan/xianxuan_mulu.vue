<template>
	<view>
		<view class="xianxuan_list">
			<view class="xianxuan" @click="choose_mokuai(0)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/jingzhunfuping.png" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">精准扶贫</text>
					<text class="enter">点击进入</text>
				</view>
			</view>
			<view class="xianxuan" @click="choose_mokuai(1)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/shidaikaimo.jpeg" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">时代楷模</text>
					<text class="enter">点击进入</text>
				</view>
			</view>
			<view class="xianxuan" @click="choose_mokuai(2)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/zhihuidangjian.jpeg" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">智慧党建</text>
					<text class="enter">点击进入</text>
				</view>
			</view>
			<view class="xianxuan"@click="choose_mokuai(3)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/zhihuihuanbao.jpeg" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">智慧环保</text>
					<text class="enter">点击进入</text>
				</view>
			</view>
			<view class="xianxuan" @click="choose_mokuai(4)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/zhihuishequ.png" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">智慧社区</text>
					<text class="enter">点击进入</text>
				</view>
			</view>
			<view class="xianxuan" @click="choose_mokuai(5)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/zhihuiyanglao.jpg" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">智慧养老</text>
					<text class="enter">点击进入</text>
				</view>
			</view>
			<view class="xianxuan" @click="choose_mokuai(6)">
				<view class="img">
					<u-image src="../../../static/myimgs/xianxuan_mokuai/zhongguozhizao.png" width="100%" height="180rpx"></u-image>
				</view>
				<view class="text">
					<text class="title">中国智造</text>
					<text class="enter">点击进入</text>
				</view>
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
			choose_mokuai(id){
				if(id==0){
					console.log(id)
				}else if(id==1){
					console.log(id)
				}
			}
		}
	}
</script>

<style scoped>
	.xianxuan_list{
		display: flex;
		flex-direction: column;
	}
	.xianxuan{
		display: flex;
		flex-direction: row;
		margin: 6rpx;
		padding: 8rpx;
		border: solid 4rpx #999;
		border-radius: 20rpx;
		background-color: #F0F8FF;
	}
	.img{
		flex: 1;
	}
	.text{
		flex: 3;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}
	.enter{
		margin-top: 20rpx;
		color: #888888;
	}
	.title{
		font-size: 40rpx;
	}
</style>
