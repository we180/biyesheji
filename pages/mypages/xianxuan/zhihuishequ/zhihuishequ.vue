<template>
	<view>
		<view class="banner u-m-20">
			<u-swiper :list="banner"></u-swiper>
		</view>
		<view class="notice u-m-20">
			<u-notice-bar :more-icon="true" :list="notice" @click="tonewsindex"></u-notice-bar>
		</view>
		<view class="type">
			<u-icon name="phone" label="物件服务" size="70" label-size="30" label-pos="bottom" @click="towujianfuwu"></u-icon>
			<u-icon name="grid" label="快件管理" size="70" label-size="30" label-pos="bottom" @click="tokuaijianguanli"></u-icon>
			<u-icon name="email" label="友邻社交" size="70" label-size="30" label-pos="bottom" @click="toshejiao"></u-icon>
			<u-icon name="bag" label="商业推广" size="70" label-size="30" label-pos="bottom" @click="totuiguang"></u-icon>
			<u-icon name="car" label="车辆管理" size="70" label-size="30" label-pos="bottom" @click="tocheliangguanli"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-section title="社区动态" :right="false" font-size="40"></u-section>
		<u-gap></u-gap>
		<view class="news">
			<view class="newsindex" @click="tonewsindex">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../static/myimgs/myimg_shequ/u=2081009638,1317666904&fm=26&fmt=auto&gp=0.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>深圳市龙岗区南湾街道办事处通知</h3>
							<text class="u-line-3">近日，南湾街道厦村社区恒大国香山花园业委会将一面“为民办事关怀至，携手共建业委会”的锦旗赠送给厦村社区党委，以感谢党委社区力排万难推进业委会成立及常态指导业委会开展工作</text>
						</view>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="newsindex" @click="tonewsindex">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../static/myimgs/myimg_shequ/u=2163698466,3692809484&fm=26&fmt=auto&gp=0.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>深圳市龙岗区南湾街道办事处</h3>
							<text class="u-line-3">为深入开展党史学习教育，吉厦社区党委深入挖掘社区优秀退役军人在各条战线上的精彩故事，让老兵故事进社区，进一步激发广大干部群众爱党爱国的热情，为建党100周年献礼</text>
						</view>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="newsindex" @click="tonewsindex">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../static/myimgs/myimg_shequ/ZhiHuiSheQu-HuoDong.jpg.jpg" width="100%" height="180rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="yizhantext">
							<h3>深圳市龙岗区南湾街道办事处通知</h3>
							<text class="u-line-3">农历新年将至，为进一步弘扬中华传统文化，近日，南岭村社区億未来儿童馆围绕“年味”开展亲子国学课堂系列活动，与社区10余对亲子一起诵读国学经典，体验“年味”国学。</text>
						</view>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[
					"../../../../static/myimgs/myimg_shequ/u=2081009638,1317666904&fm=26&fmt=auto&gp=0.jpg",
					"../../../../static/myimgs/myimg_shequ/u=2163698466,3692809484&fm=26&fmt=auto&gp=0.jpg"
				],
				notice:[
					"2022/12/7 16:45 深圳市龙岗区南湾街道办事处通知:近日，南湾街道厦村社区恒大国香山花园业委会将一面“为民办事关怀至，携手共建业委会”的锦旗赠送给厦村社区党委，以感谢党委社区力排万难推进业委会成立及常态指导业委会开展工作。"
				],
			}
		},
		methods: {
			towujianfuwu(){
				uni.navigateTo({
					url:'wujianguanli/wujianguanli'
				})
			},
			tokuaijianguanli(){
				uni.navigateTo({
					url:'kuaijianguanli/kuaijianguanli'
				})
			},
			toshejiao(){
				uni.navigateTo({
					url:'shejiao/shejiao'
				})
			},
			totuiguang(){
				uni.navigateTo({
					url:'tuiguang/tuiguang'
				})
			},
			tocheliangguanli(){
				uni.navigateTo({
					url:'cheliangguanli/cheliangguanli'
				})
			},
			tonewsindex(){
				uni.navigateTo({
					url:'shequ_index'
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
	}
	.yizhantext{
		display: flex;
		flex-direction: column;
	}
</style>
