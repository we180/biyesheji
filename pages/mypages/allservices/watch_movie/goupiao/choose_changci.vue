<template>
	<view>
		<view class="yingyuaninfo">
			<!-- 包括：影院名称、地址 -->
			<h3>影院名称:{{yingyuan_name}}</h3>
			<h3>地址:{{yingyuan_name}}</h3>
			
		</view>
		<u-gap></u-gap>
		<view class="movieinfo">
			<!-- 中部显示影片信息，包括：封面、名称、评分 -->
			<u-image width="100%" height="300rpx" :src="baseUrl+movie.cover"></u-image>
			<h3 style="text-align: center;">{{movie.name}}</h3>
			<h3>评分:{{movie.score}}</h3>
		</view>
		<view class="changci_list" v-for="(item,changciid) in changci" :key="changciid">
			<!-- 场次信息包括：开始时间、散场时间、影片类型、播放类型、价格以及购票按钮，点击“购票”按钮进入选座页面。 -->
			<text>开始时间:{{item.startTime}}</text>
			<text>散场时间:{{item.endTime}}</text>
			<text>影片类型:{{item.playType}}</text>
			<text>播放类型:{{item.playType}}</text>
			<text>价格:{{item.price}}元</text>
			<u-button type="success" @click="togoupiao(changciid)">购票</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				movie:'',
				movie_id:'',
				yingyuan_name:'',
				yingyuan:'',
				yingyuan_id:'',
				changci:[]
			}
		},
		methods: {
			togoupiao(id){
				// uni.navigateTo({
				// 	url:'xuanzuo?roomid='+this.changci[id].id
				// })
				uni.navigateTo({
					url:'xuanzuo_2'
				})
			},
			async getData(){
				// let res1=await this.$u.get('/prod-api/api/movie/theatre/'+this.yingyuan_id)
				// this.yingyuan=res1.data
				// console.log(res1);
				// console.log(this.yingyuan_id);
				let res2=await this.$u.get('/prod-api/api/movie/film/detail/'+this.movie_id)
				this.movie=res2.data
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/movie/theatre/times/list?movieId='+this.movie_id)
				this.changci=res3.rows
				console.log(res3);
			}
		},
		onLoad(ops) {
			this.movie_id=ops.movie_id
			this.yingyuan_name=ops.yingyuan_name
			this.yingyuan_id=ops.yingyuan_id
			this.getData()
		}
	}
</script>

<style scoped>
	.changci_list{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
