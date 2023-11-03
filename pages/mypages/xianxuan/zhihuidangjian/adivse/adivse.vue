<template>
	<view>
		<view class="">
			<view class="advise" v-for="(item,index) in adviselist" :key="index">
				<text>姓名:{{item.name}}</text>
				<text>手机号:{{item.phone}}</text>
				<text>内容:{{item.content}}</text>
			</view>
		</view>
		<view class="submit">
			<u-button type="success" @click="toadd">创建问题/建议</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showpop:false,
				action:"http://192.168.23.91:10001/prod-api/common/upload",
				name:'',
				phone:'',
				content:''
			}
		},
		methods: {
			toadd(){
				uni.navigateTo({
					url:'addadvise'
				})
			}
		},
		onLoad() {
			this.$forceUpdate()
			console.log(this.adviselist);
		}
	}
</script>

<style scoped>
	.submit{
		position: fixed;
		bottom: 0rpx;
		width: 100%;
		padding: 20rpx;
	}
	.advise{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
</style>
