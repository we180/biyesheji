<template>
	<view>
		<view class="library" v-for="(item,libraryid) in library" :key="libraryid" @click="tolibrary_De(libraryid)">
			<!-- 图书馆名称、图书馆具体地址、营业时间和营业状态，营业中的图书馆将优先展示 -->
			<h3>{{item.name}}</h3>
			<text>图书馆具体地址:{{item.address}}</text>
			<text>营业时间:{{item.businessHours}}</text>
			<text>营业状态:{{item.businessState=='1'?'营业中':'暂停营业'}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				library:[]
			}
		},
		methods: {
			tolibrary_De(id){
				uni.navigateTo({
					url:'library_details?id='+this.library[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/digital-library/library/list')
				this.library=res1.rows
				console.log(res1); 
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.library{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
