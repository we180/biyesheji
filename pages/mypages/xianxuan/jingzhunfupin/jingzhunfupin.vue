<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner"></u-swiper>
		</view>
		 <view class="type">
			 <u-icon name="file-text" label="新闻" label-pos="bottom" size="100" color="#2979ff" @click="tonewslist"></u-icon>
			 <u-icon name="order" label="扶贫案例" label-pos="bottom" size="100" color="#2979ff" @click="toanli"></u-icon>
			 <u-icon name="photo" label="村情村貌" label-pos="bottom" size="100" color="#2979ff" @click="tocunqing"></u-icon>
			 <u-icon name="android-fill" label="工作台" label-pos="bottom" size="100" color="#2979ff" @click="towork"></u-icon>
		 </view>
		 <u-gap></u-gap>
		 <u-section title="最新新闻" font-size="40"></u-section>
		 <u-gap></u-gap>
		 <view class="newslist">
		 	<view class="news">
		 		<view class="newsindex">
		 			<u-row>
		 				<u-col span="4">
		 					<u-image src="../../../../static/myimgs/myimg_fupin/368cab1c600c364ef27d27c6e1bc0656@2x.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
		 				</u-col>
		 				<u-col span="8">
		 					<h3>开阳信息锁进：饮水思源，精准扶贫</h3>
		 					<text class="u-line-2">近日，秦峰镇新塘村村民委员会为感谢锁进先生为秦峰镇新塘村的扶贫事业做出的杰出贡献，特聘锁进先生为新塘村的“名誉村主任”。锁进先生是江西渝网科技股份有限公司董事长，上饶开阳即渝网旗下全资子公司，此前一直专注于扶贫事业，经商的同时不忘回馈社会，积极履行应尽的社会责任，呼吁更多社会人士共同营造互相关心、互相帮助、互相支持的良好社会氛围。</text>
		 					<text>2022/12/10</text>
		 				</u-col>
		 			</u-row>
		 		</view>
		 	</view>
		 </view>
		 <u-gap></u-gap>
		 <view class="newslist" >
		 	<view class="news">
		 		<view class="newsindex">
		 			<u-row>
		 				<u-col span="4">
		 					<u-image src="../../../../static/myimgs/myimg_fupin/2.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
		 				</u-col>
		 				<u-col span="8">
		 					<h3>常德联通：精准扶贫暖人心 感恩帮扶送锦旗</h3>
		 					<text class="u-line-2">“吃饭莫忘种田人，吃水不忘挖井人，非常感谢常德联通驻村工作队人员的辛勤付出”。近日，常德汉寿县洞庭村村委一行5人，将一面写有“联通扶贫用真情 洞庭人民永记心”的锦旗专程送到常德联通</text>
		 					<text>2022/12/10</text>
		 				</u-col>
		 			</u-row>
		 		</view>
		 	</view>
		 </view>
		 <u-gap></u-gap>
		 <view class="newslist" >
		 	<view class="news">
		 		<view class="newsindex">
		 			<u-row>
		 				<u-col span="4">
		 					<u-image src="../../../../static/myimgs/myimg_fupin/3.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
		 				</u-col>
		 				<u-col span="8">
		 					<h3>中脉不惧虚假宣传谣言，毅然进山精准扶贫</h3>
		 					<text class="u-line-2">中脉科技配合四川省工商局精准扶贫项目捐赠仪式在四川省巴中市南江县关门乡白果树村村委会隆重举行。中共南江县委常委/南江县副县长全韬、南江县关门乡白果树村第一书记刘支书等当地政府领导出席了捐赠仪式。</text>
		 					<text>2022/12/10</text>
		 				</u-col>
		 			</u-row>
		 		</view>
		 	</view>
		 </view>
		 <u-gap></u-gap>
		 <view class="newslist" >
		 	<view class="news">
		 		<view class="newsindex">
		 			<u-row>
		 				<u-col span="4">
		 					<u-image src="../../../../static/myimgs/myimg_fupin/4.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
		 				</u-col>
		 				<u-col span="8">
		 					<h3>“甘肃省脱贫攻坚先进个人”黄健，引领燕之屋精准扶贫</h3>
		 					<text class="u-line-2">中国的扶贫故事，是一部波澜壮阔的奋斗史。改革开放以来，中国让7亿人走出了贫困。燕之屋交出了“特色扶贫”的成绩单，在中国扶贫史上留下了厚重的一页。</text>
		 					<text>2022/12/10</text>
		 				</u-col>
		 			</u-row>
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
					"../../../../static/myimgs/myimg_fupin/368cab1c600c364ef27d27c6e1bc0656@2x.png",
					"../../../../static/myimgs/myimg_fupin/6f04d3d379515f0942bd0330f901df37@2x.png",
					"../../../../static/myimgs/myimg_fupin/8abe3f56303248033f031f01f7522700@2x.png"
				],
			}
		},
		methods: {
			tonewslist(){
				uni.navigateTo({
					url:'news/newslist'
				})
			},
			toanli(){
				uni.navigateTo({
					url:'anli/anli'
				})
			},
			tocunqing(){
				uni.navigateTo({
					url:'cunqing/cunqing'
				})
			},
			towork(){
				uni.navigateTo({
					url:'work/work'
				})
			},
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		flex-wrap: wrap;
	}
	.type>*{
		width: 25%;
		padding: 20rpx;
	}
	.news{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 4rpx solid;
		border-radius: 20rpx;
	}
</style>
