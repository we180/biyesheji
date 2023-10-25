<template>
	<view>
		<view class="info" style="display: flex;flex-direction: column;">
			<!-- 页面展示新闻资讯轮播、公司简介、运输方式介绍、运费介绍信息。 -->
			<u-image width="100%" height="300rpx" :src="baseUrl+info.imgUrl"></u-image>
			<h3 style="text-align: center;">{{info.name}}</h3>
			<text>{{info.introduce}}</text>
			<text>运输方式介绍:{{info.shippingMethod}}</text>
			<text>运费介绍:{{info.priceList}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				info:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/logistics-inquiry/logistics_company/'+this.id)
				this.info=res1.data
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>

</style>
