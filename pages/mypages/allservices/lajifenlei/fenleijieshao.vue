<template>
	<view>
		<view class="info1" v-if="id==8" v-for="(item,infoid) in info.slice(0,1)" :key="infoid">
			<!-- 顶部左侧为正方形分类图标，右侧为分类说明，分类介绍页下部为投放要求。 -->
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="230rpx" :src="baseUrl+item.imgUrl"></u-image> 
				</u-col>
				<u-col span="8">
					<h3>分类说明</h3>
					<text>{{item.introduce}}</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<h3>投放要求</h3>
			<text>{{item.guide}}</text>
		</view>
		<view class="info1" v-if="id==9" v-for="(item,infoid) in info.slice(1,2)" :key="infoid+999">
			<!-- 顶部左侧为正方形分类图标，右侧为分类说明，分类介绍页下部为投放要求。 -->
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="230rpx" :src="baseUrl+item.imgUrl"></u-image> 
				</u-col>
				<u-col span="8">
					<h3>分类说明</h3>
					<text>{{item.introduce}}</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<h3>投放要求</h3>
			<text>{{item.guide}}</text>
		</view>
		<view class="info1" v-if="id==10" v-for="(item,infoid) in info.slice(2,3)" :key="infoid+99">
			<!-- 顶部左侧为正方形分类图标，右侧为分类说明，分类介绍页下部为投放要求。 -->
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="230rpx" :src="baseUrl+item.imgUrl"></u-image> 
				</u-col>
				<u-col span="8">
					<h3>分类说明</h3>
					<text>{{item.introduce}}</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<h3>投放要求</h3>
			<text>{{item.guide}}</text>
		</view>
		<view class="info1" v-if="id==11" v-for="(item,infoid) in info.slice(3,4)" :key="infoid+9">
			<!-- 顶部左侧为正方形分类图标，右侧为分类说明，分类介绍页下部为投放要求。 -->
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="230rpx" :src="baseUrl+item.imgUrl"></u-image> 
				</u-col>
				<u-col span="8">
					<h3>分类说明</h3>
					<text>{{item.introduce}}</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<h3>投放要求</h3>
			<text>{{item.guide}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info:[],
				id:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/garbage-classification/garbage-classification/list')
				this.info=res1.rows
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			console.log(this.id);
			this.getData()
		}
	}
</script>

<style scoped>

</style>
