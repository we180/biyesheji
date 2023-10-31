<template>
	<view>
		<view class="zuoweilist">
			<view class="zuowei" v-for="(item,zuoweiid) in zuowei" :key="zuoweiid">
				<u-icon name="map" color="#2979ff" size="77" :label="item.row+'-'+item.col" label-pos="bottom" label-size="36" @click="clickicon(zuoweiid)"></u-icon>
			</view>
		</view>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<view class="text">
			<h2 style="text-align: center;">已选择:{{xuanze}}</h2>
			<u-button @click="queding" type="success">确定</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				zuowei:'',
				xuanze:''
			}
		},
		methods: {
			queding(){
				uni.navigateTo({
					url:'getcode'
				})
			},
			clickicon(id){
				this.xuanze=this.zuowei[id].row+'-'+this.zuowei[id].col
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/theatre/seat/list?roomId='+this.id)
				this.zuowei=res1.rows
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.roomid
			this.getData()
		},
	}
</script>

<style scoped>
	.zuoweilist{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: space-around;
	}
	.zuowei{
		width: 20%;
	}
	.text{
		background-color: #C8C9CC;
		position: fixed;
		bottom: 10rpx;
		padding: 10rpx;
		width: 100%;
	}
</style>
