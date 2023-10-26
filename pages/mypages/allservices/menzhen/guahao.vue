<template>
	<view>
		<view class="type">
			<u-tabs :current="current" :list="typelist" @change="changetype"></u-tabs>
		</view>
		
		<view class="putong" v-if="index_flag==0">
			<view class="yuyuelist" v-for="(item,yuyuelistid) in yuyuelist" :key="yuyuelistid">
				<span>姓名:{{item.patientName}}</span>
				<span>金额:{{item.money}}</span>
				<span>门诊名称:{{item.categoryName}}</span>
				<span>预约时间:{{item.reserveTime}}</span>
			</view>
			<view class="add_card">
				<image src="../../../../static/uview/example/min_button_select.png" mode="" @click="addcard"></image>
			</view>
		</view>
		<view class="zhuanjia" v-if="index_flag==1">
			<h1>暂无数据</h1>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				current:0,
				index_flag:'',
				typelist:[
					{
						name:'普通'
					},
					{
						name:'专家'
					}
				],
				yuyuelist:[]
			}
		},
		methods: {
			addcard(){
				uni.navigateTo({
					url:'new_guahao'
				})
			},
			changetype(index){
				this.current=index
				this.index_flag=index
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/hospital/reservation/list')
				this.yuyuelist=res1.rows
				console.log(res1);
			}
		},
		created() {
			this.getData()
		},
		onLoad(options) {
			this.id=options.id
		}
	}
</script>

<style scoped>
	.type{
		text-align: center;
	}
	h1{
		text-align: center;
		opacity: 0.6;
		margin-top: 50rpx;
	}
	.add_card {
		position: fixed;
		bottom: 0rpx;
		right: 39.5%;
	}
	
	.add_card image {
		width: 150rpx;
		height: 150rpx;
	}
	.yuyuelist{
		display: flex;
		flex-direction: column;	
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: solid 4rpx pink;
		box-shadow: 8rpx 8rpx 16rpx skyblue;
		background-color: aliceblue;
	}
</style>
