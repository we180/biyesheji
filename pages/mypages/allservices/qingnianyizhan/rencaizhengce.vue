<template>
	<view>
		<view class="head">
			<u-image width="100%" height="400rpx" :src="baseUrl+rencaiquyu_de.imgUrl"></u-image>
			<text>{{rencaiquyu_de.introduce}}</text>
		</view>
		<h2 style="text-align: center;">人才政策文件列表</h2>
		<view class="zhengcelist" v-for="(item,zhengcelistid) in zhengcelist" :key="zhengcelistid" @click="tozhengce_De(zhengcelistid)">
			<h3 style="text-align: center;">{{item.title}}</h3>
			<h4 style="text-align: center;">{{item.createTime}}</h4>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				zhengcelist:[],
				rencaiquyu_de:''
			}
		},
		methods: {
			tozhengce_De(id){
				uni.navigateTo({
					url:'zhengce_details?id='+this.zhengcelist[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/youth-inn/talent-policy/list?areaId='+this.id)
				this.zhengcelist=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/youth-inn/talent-policy-area/'+this.id)
				this.rencaiquyu_de=res2.data
				console.log(res2);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.head{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
	.zhengcelist{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
