<template>
	<view>
		<view class="kaimolist" v-for="(item,kaimoid) in 2" :key="kaimoid">
			<view class="kaimo">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/W020211011361082030178.png" width="100%"
							height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>楷模介绍</h3>
						<text class="u-line-5">孙景坤在革命战争年代冲锋陷阵、不怕牺牲。在解放战争中，他先后参加四平战役、辽沈战役、平津战役、解放长沙战役和解放海南岛战役，荣立二等功两次、三等功一次，被授予解放东北纪念章、解放华北纪念章、解放华中南纪念章和解放海南岛纪念章</text>
					</u-col>
				</u-row>
			</view>
		</view>
		<view class="huodonglist" v-for="(item,huodongid) in 3" :key="huodongid+10">
			<view class="huodong">
				<u-image src="../../../../../static/myimgs/myimg_kaimo/597403047627b05a75c3dd.jpg" width="100%" height="220rpx"></u-image>
				<h2>金银花药材种植</h2>
				<h4>发起人:平顺县新的社会阶层人士联谊会</h4>
				<h4>活动简介:金银花药材种植项目</h4>
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
			
		}
	}
</script>

<style scoped>
	.kaimo {
		margin: 10rpx;
		padding: 10rpx;
		border: solid 2rpx #CCC;
		border-radius: 20rpx;
	}
	.huodong{
		margin: 10rpx;
		padding: 10rpx;
		display: flex;
		flex-direction: column;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
