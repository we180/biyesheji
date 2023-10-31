<template>
	<view>
		<!-- 信息包括标题、日期、内容和发布者。 -->
		<view class="text">
			<h2 style="text-align: center;">{{zhengce.title}}</h2>
			<h3 style="text-align: center;">{{zhengce.createTime}}</h3>
			<rich-text :nodes="zhengce.content"></rich-text>
			<h3 style="text-align: center;">{{zhengce.author}}</h3>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				zhengce:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/youth-inn/talent-policy/'+this.id)
				this.zhengce=res1.data
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
	.text{
		padding: 10rpx;
		margin: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
