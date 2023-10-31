<template>
	<view>
		<view class="info">
			<u-image width="100%" height="300rpx" :src="baseUrl+yingyuan.cover"></u-image>
			<h2 style="text-align: center;">{{yingyuan.name}}</h2>
			<h3>地址:{{yingyuan.address}}</h3>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				yingyuan:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/theatre/'+this.id)
				this.yingyuan=res1.data
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
