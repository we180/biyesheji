<template>
<!-- 1.进入爱心捐赠主页面，页面显示返回上一页按钮，搜索输入框、广告轮播图、捐赠次数和实时捐赠列表、公益分类、推荐公益列表。
(1)搜索输入框：输入搜索内容后，点击软键盘“搜索”按钮，跳转至搜索结果公益列表页面，列表内容包括公益类别、公益名称、发布人、已筹善款、项目时间和参与人数。
(2)广告轮播图：每间隔3秒切换广告图。
(3)公益分类：以图标和名称为单元格方式显示，手机端显示4个，共两行，每个类目入口布局显示为圆形图标和名称，点击图标可以进入对应公益分类列表页面。
(4)推荐公益列表项：公益分类图标下面显示推荐公益，类别名称下方显示公益图片、公益项目名称、发布组织、捐赠人数和已筹善款。 -->
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<view class="typeall">
			<view class="type" v-for="(item,typeid) in type" :key="typeid" @click="tolist(typeid)">
				<u-icon :name="baseUrl+item.imgUrl" :label="item.name" label-pos="bottom" size="60"></u-icon>
			</view>
		</view>
		<u-gap></u-gap>
		<u-section :right="false" title="推荐公益" font-size="40"></u-section>
		<view class="recommend" v-for="(item,recommendid) in recommend" :key="recommendid">
			<view class="reimg">
				<image :src="baseUrl+item.imgUrl" mode=""></image>
			</view>
			<view class="retext">
				<h3>{{item.name}}</h3>
				<text>发布组织：{{item.author}}</text>
				<text>捐赠人数：{{item.donateCount}}</text>
				<text>已筹善款：{{item.moneyNow}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				type:[],
				recommend:[]
			}
		},
		methods: {
			search(index){
				uni.navigateTo({
					url:'gongyi_list'
				})
			},
			tolist(id){
				uni.navigateTo({
					url:'gongyi_list?id='+this.type[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/public-welfare/ad-banner/list')
				this.banner=res1.data.map((res)=>{
					return{
						image:this.baseUrl+res.imgUrl
					}
				})
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/public-welfare/public-welfare-type/list')
				this.type=res2.data
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/public-welfare/public-welfare-activity/recommend-list')
				this.recommend=res3.rows
				console.log(res3);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.typeall{
		display: flex;
		flex-wrap: wrap;
		flex-direction: row;
	}
	.type{
		width: 25%;
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 10rpx;
	}
	.recommend{
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border: #A0CFFF 2rpx solid;
	}
	.reimg image{
		width: 220rpx;
		height: 220rpx;
	}
	
	.retext{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
	}
</style>
