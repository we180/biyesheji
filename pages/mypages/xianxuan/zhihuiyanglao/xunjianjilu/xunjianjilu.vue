<template>
	<view>
		<view class="head">
			<u-subsection active-color="#ff9900" :list="list" :current="current" @change="changetab"></u-subsection>
		</view>
		<view class="xunjianlist" v-if="current==0">
			<view class="xunjian">
				<h2 class="u-m-10">2022.12.9</h2>
				<view class="xunjianinfo">
					<h3>8:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">加肯特</text>
						<text class="u-tips-color">营养师</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;" @click="pingjia">评价</u-button>
					</view>
					<text>厨房整洁，厕所整洁，卧室地面干净，房间内垃圾已处理，老人各项状态正常，环境稳定</text>
				</view>
				<view class="xunjianinfo">
					<h3>12:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">缪恩</text>
						<text class="u-tips-color">营养师</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>厨房整洁，厕所整洁，卧室地面干净，房间内垃圾已处理，老人各项状态正常，环境稳定</text>
				</view>
				<view class="xunjianinfo">
					<h3>4:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">冷峰</text>
						<text class="u-tips-color">营养师</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>厨房整洁，厕所整洁，卧室地面干净，房间内垃圾已处理，老人各项状态正常，环境稳定</text>
				</view>
			</view>

			<view class="xunjian">
				<h2 class="u-m-10">2022.12.10</h2>
				<view class="xunjianinfo">
					<h3>8:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">青雀</text>
						<text class="u-tips-color">营养师</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>厨房整洁，厕所整洁，卧室地面干净，房间内垃圾已处理，老人各项状态正常，环境稳定</text>
				</view>
				<view class="xunjianinfo">
					<h3>12:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">艾伦</text>
						<text class="u-tips-color">营养师</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>厨房整洁，厕所整洁，卧室地面干净，房间内垃圾已处理，老人各项状态正常，环境稳定</text>
				</view>
				<view class="xunjianinfo">
					<h3>4:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">埃斯蒂尼安</text>
						<text class="u-tips-color">营养师</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>厨房整洁，厕所整洁，卧室地面干净，房间内垃圾已处理，老人各项状态正常，环境稳定</text>
				</view>
			</view>
		</view>
		
		<view class="xunjianlist" v-if="current==1">
			<view class="xunjian">
				<h2 class="u-m-10">2022.12.9</h2>
				<view class="xunjianinfo">
					<h3>8:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">娜娜莫</text>
						<text class="u-tips-color">助手</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;" @click="pingjia">评价</u-button>
					</view>
					<text>总热量约1.8kj，包含豆浆，红米粥，红烧肉，茶叶蛋，红烧茄子，烧烤暗色茄子，苹果</text>
				</view>
				<view class="xunjianinfo">
					<h3>12:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">劳班</text>
						<text class="u-tips-color">助手</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>总热量约1.7kj，包含豆浆，红米粥，梅菜扣肉，蜜浸火龙果，红烧茄子，麻婆豆腐，苹果</text>
				</view>
				<view class="xunjianinfo">
					<h3>4:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">莫莫蒂</text>
						<text class="u-tips-color">助手</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>总热量约1.9kj，包含豆浆，红米粥，红烧肉，茶叶蛋，红烧茄子，麻婆豆腐，苹果</text>
				</view>
			</view>
		
			<view class="xunjian">
				<h2 class="u-m-10">2022.12.10</h2>
				<view class="xunjianinfo">
					<h3>8:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">阿尔菲诺</text>
						<text class="u-tips-color">助手</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>总热量约1.5kj，包含豆浆，红米粥，红烧肉，近东虾香饭，番茄炒鸡蛋，麻婆豆腐，苹果</text>
				</view>
				<view class="xunjianinfo">
					<h3>12:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">宝山</text>
						<text class="u-tips-color">助手</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>总热量约1.9kj，包含豆浆，红米粥，红烧肉，镶烤墨鱼，红烧蛋，麻婆苹果，豆腐</text>
				</view>
				<view class="xunjianinfo">
					<h3>4:30</h3>
					<view>
						<text style="font-size: 40rpx;margin-right: 20rpx;">莫古唐</text>
						<text class="u-tips-color">助手</text>
						<u-button type="primary" size="mini" style="float: right;width: 150rpx;"  @click="pingjia">评价</u-button>
					</view>
					<text>总热量约1.8kj，包含豆浆，红米粥，红烧肉，茶叶蛋，红烧茄子，麻婆豆腐，南瓜浓汤</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{
						name: '巡检记录'
					},
					{
						name: '餐饮服务记录'
					}
				],
				current: 0
			}
		},
		methods: {
			changetab(index) {
				this.current = index
			},
			pingjia(){
				uni.navigateTo({
					url:'xunjian_pingjia'
				})
			},
		}
	}
</script>

<style scoped>
	.xunjianinfo {
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
</style>
