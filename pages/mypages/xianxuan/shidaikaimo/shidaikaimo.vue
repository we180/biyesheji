<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="type">
			<u-icon name="order" color="#2979ff" size="86" label="楷模列表" label-pos="bottom" label-size="32" @click="tokaimo_list"></u-icon>
			<u-icon name="bookmark" color="#2979ff" size="86" label="英雄故事" label-pos="bottom" label-size="32" @click="tohero_story"></u-icon>
			<u-icon name="edit-pen" color="#2979ff" size="86" label="学习心得" label-pos="bottom" label-size="32" @click="toxuexixinde"></u-icon>
			<u-icon name="grid" color="#2979ff" size="86" label="公益活动" label-pos="bottom" label-size="32" @click="tohuodong"></u-icon>
			<u-icon name="list-dot" color="#2979ff" size="86" label="身边的英雄" label-pos="bottom" label-size="32" @click="tonearhero"></u-icon>
		</view>
		<u-gap></u-gap>
		<view class="list">
			<view class="kaimolist">
				<u-section title="时代楷模精神" font-size="40" :right="false"></u-section>
				<view class="kaimo">
					<u-row>
						<u-col span="4">
							<u-image src="../../../../static/myimgs/myimg_kaimo/W020211011361082030178.png" width="100%"
								height="250rpx"></u-image>
						</u-col>
						<u-col span="8">
							<h3>楷模介绍</h3>
							<text class="u-line-5">孙景坤在革命战争年代冲锋陷阵、不怕牺牲。在解放战争中，他先后参加四平战役、辽沈战役、平津战役、解放长沙战役和解放海南岛战役，荣立二等功两次、三等功一次，被授予解放东北纪念章、解放华北纪念章、解放华中南纪念章和解放海南岛纪念章</text>
						</u-col>
					</u-row>
					<u-gap></u-gap>
					<u-row>
						<u-col span="4">
							<u-image src="../../../../static/myimgs/myimg_kaimo/1.png" width="100%"
								height="250rpx"></u-image>
						</u-col>
						<u-col span="8">
							<h3>楷模介绍</h3>
							<text class="u-line-5">杜富国是陆军某扫雷排爆大队战士。入伍以来，他始终把忠诚和信仰刻在心中，把使命和责任扛在肩上，主动请缨征战雷场，苦练精练过硬本领，为人民利益和边境安宁挥洒热血，在平凡岗位干出了突出业绩。2018年10月11日，杜富国随队参加排雷作业时，危急时刻冲锋在前，为保护战友身受重伤，失去双眼和双手。杜富国同志曾先后获得“全国自强模范”“感动中国十大人物”、陆军“四有”新时代革命军人标兵等称号，荣立个人一等功。</text>
						</u-col>
					</u-row>
				</view>
			</view>
			<view class="huodonglist">
				<u-section title="往期公告" font-size="40" :right="false"></u-section>
					<view class="huodong">
						<u-image src="../../../../static/myimgs/myimg_kaimo/597403047627b05a75c3dd.jpg" width="100%" height="220rpx"></u-image>
						<h2>金银花药材种植</h2>
						<h4>发起人:平顺县新的社会阶层人士联谊会</h4>
						<h4>活动简介:金银花药材种植项目</h4>
					</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[
					"../../../../static/myimgs/myimg_kaimo/597403047627b05a75c3dd.jpg",
					"../../../../static/myimgs/myimg_kaimo/665014142627b085436522.jpg",
					"../../../../static/myimgs/myimg_kaimo/924186256627b06ff87637.jpg",
					"../../../../static/myimgs/myimg_kaimo/924692398627b067043585.png"
				],
			}
		},
		methods: {
			tokaimo_list(){
				uni.navigateTo({
					url:'kaimo_list/kaimo_list'
				})
			},
			tohero_story(){
				uni.navigateTo({
					url:'hero_story/hero_story'
				})
			},
			toxuexixinde(){
				uni.navigateTo({
					url:'xuexixinde/xuexixinde'
				})
			},
			tohuodong(){
				uni.navigateTo({
					url:'gongyihuodong/gongyihuodong'
				})
			},
			tonearhero(){
				uni.navigateTo({
					url:'nearhero/nearhero'
				})
			},
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-around;
	}
	.kaimo{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
	.huodong{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
