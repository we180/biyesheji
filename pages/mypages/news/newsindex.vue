<template>
	<view>
		<view class="news">
			<u-image width="100%" height="400rpx" :src="baseUrl+news.cover"></u-image>
			<h2>{{news.title}}</h2>
			<rich-text :nodes="news.content"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				news:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/press/press/'+this.id)
				this.news=res1.data
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
	.news{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #999 2rpx solid;
	}
</style>
