<template>
	<view>
		<view class="tousulist" v-for="(item,tousulistid) in tousulist" :key="tousulistid">
			<text>公司名称:{{item.company==null?'未选择':item.company.name}}</text>
			<text>运单号:{{item.infoNo}}</text>
			<text class="u-line-3">投诉内容:{{item.description}}</text>
		</view>
		<view class="news++">
			<u-button type="primary" @click="addnew">新增</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tousulist:[]
			}
		},
		methods: {
			addnew(){
				uni.navigateTo({
					url:'tousuxinzeng'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/logistics-inquiry/logistics_complaint/my-list')
				this.tousulist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.tousulist{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
