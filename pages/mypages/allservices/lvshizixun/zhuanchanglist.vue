<template>
	<view>
		<view class="typelist">
			<view class="type" v-for="(item,typeid) in type" :key="typeid" @click="tolvshilist(typeid)">
				<u-icon :name="baseUrl+item.imgUrl" size="66" label-pos="bottom" :label="item.name"></u-icon>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type:[]
			}
		},
		methods: {
			tolvshilist(id){
				uni.navigateTo({
					url:'lvshilist?id='+this.type[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/lawyer-consultation/legal-expertise/list')
				this.type=res1.rows.sort((a,b)=>{
					return b.sort-a.sort
				})
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.typelist{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.type{
		display: flex;
		justify-content: center;
		align-items: center;
		width: 25%;
		margin-top: 25rpx;
	}
</style>
