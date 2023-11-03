<template>
	<view>
		<view class="info">
			<u-section title="楷模介绍" :right="false" font-size="40"></u-section>
			<view class="infotext">
				<text>孙景坤在革命战争年代冲锋陷阵、不怕牺牲。在解放战争中，他先后参加四平战役、辽沈战役、平津战役、解放长沙战役和解放海南岛战役，荣立二等功两次、三等功一次，被授予解放东北纪念章、解放华北纪念章、解放华中南纪念章和解放海南岛纪念章。在抗美援朝战争中，孙景坤参加了一系列战役，特别是在上甘岭战役中英勇作战、坚守阵地，荣获一等功一次、三等功一次，1953年6月被授予抗美援朝一级战士荣誉勋章，同年7月他作为中国人民志愿军回国英雄报告团成员受到了毛泽东等党和国家领导人的亲切接见。2020年10月14日被授予“时代楷模”称号。</text>
			</view>
		</view>
		<view class="video">
			<u-section title="楷模事迹视频" :right="false" font-size="40"></u-section>
			<u-gap></u-gap>
			<video src="../../../../../static/myimgs/myimg_kaimo/video03.mp4" controls style="width: 100%;"></video>
		</view>
		<view class="zhijing">
			<u-button type="success" @click="zhijing"><text style="font-size: 40rpx;">致敬</text></u-button>
		</view>
		<view class="pinlun">
			<u-section title="评论一下" :right="false" font-size="40"></u-section>
			<view class="pinlun_in">
				<u-input type="textarea" style="height: 220rpx;" border="border" v-model="content"></u-input>
				<u-button type="success" @click="pinlun">发表评论</u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content:''
			}
		},
		methods: {
			zhijing(){
				this.$u.toast('致敬成功')
			},
			pinlun(){
				this.$u.toast('评论成功')
				this.content=''
			},
		}
	}
</script>

<style scoped>
	.infotext{
		margin: 10rpx;
		padding: 10rpx;
		border: solid 2rpx #CCC;
		border-radius: 20rpx;
	}
	.zhijing{
		padding: 16rpx;
	}
	.pinlun_in{
		padding: 16rpx;
	}
</style>
