<template>
	<view>
		<view class="head">
			<u-navbar title="生活交费">
				<u-icon name="order" color="#2979ff" size="60" label="交费历史" slot="right" style="margin-right: 20rpx;" @click="tojiaofei_history"></u-icon> 
			</u-navbar> 
		</view>
		<view class="yunyingshang">
			<u-field v-model="yunyingshang" label="运营商" @click="showyunying=true"></u-field> 
			<u-action-sheet :list="list" @click="chooseyunying" v-model="showyunying"></u-action-sheet>
			<u-field v-model="phone" label="手机号码"></u-field>
			<u-button type="primary" @click="search">查询</u-button>
		</view>
		<u-gap></u-gap>
		<u-section title="常用手机号列表" font-size="40" :right="false"></u-section>
		<!-- 运营商名称、手机号、添加时间，点击行进入交费页面 -->
		<view class="phonelist" @click="search">
			<h3>运营商:中国电信</h3>
			<h3>手机号:1135468435</h3>
			<h3>添加时间:2023/2/1</h3>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yunyingshang:'',
				showyunying:false,
				phone:'',
				list:[
					{
						text:'中国移动'
					},
					{
						text:'中国电信'
					},
					{
						text:'中国联通'
					}
				]
			}
		},
		methods: {
			tojiaofei_history(){
				uni.navigateTo({
					url:'jiaofei_history'
				})
			},
			search(){
				uni.navigateTo({
					url:'jiaofei?phone='+this.phone
				})
			},
			chooseyunying(index){
				if(index==0){
					this.yunyingshang='中国移动'
				}else if(index==1){
					this.yunyingshang='中国电信'
				}else{
					this.yunyingshang='中国联通'
				}
			},
		}
	}
</script>

<style scoped>
	.phonelist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
