<template>
	<view>
		<view class="type">
			<view class="typelist" v-for="(item,typelistid) in typelist" :key="typelistid">
				<u-icon :name="baseUrl+item.imgUrl" :label="item.serviceName" label-pos="bottom" size="80" label-size="25rpx" @click="clickicon(typelistid)"></u-icon>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				typelist:[]
			}
		},
		methods: {
			clickicon(id){
				if(id==8){
					uni.navigateTo({
						url:'car_park/car_park'
					})
				}else if(id==15){
					uni.navigateTo({
						url:'find_house/find_house'
					})
				}else if(id==9){
					uni.navigateTo({
						url:'city_metor/city_metor'
					})
				}else if(id==20){
					uni.navigateTo({
						url:'wuliuchaxun/wuliuchaxun'
					})
				}
				else{
					console.log(id);
				}
			},
			async getData(){
				let res2=await this.$u.get('/prod-api/api/service/list')
				console.log(res2);
				this.typelist=res2.rows
				this.typelist.sort(function(a,b){
					return a.sort-b.sort
				})
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.typelist{
		display: flex;
		width: 20%;
		justify-content: center;
		align-items: center;
		margin-bottom: 20rpx;
	}
</style>
