<template>
	<view>
		<view class="moiveinfo">
			<!-- 页面上方显示影片信息，包括：影片封面、影片名称、评分、类型、上映时间、时长 -->
			<u-image width="100%" height="300rpx" :src="baseUrl+yingpian.cover"></u-image>
			<view class="moivetext">
				<h3>{{yingpian.name}}</h3>
				<text>评分:{{yingpian.score}}</text>
				<text>类型:{{yingpian.category}}</text>
				<text>上映时间:{{yingpian.playDate}}</text>
				<text>时长:{{yingpian.duration}}分钟</text>
			</view>
		</view>
		<u-section title="上映此影片影院列表" font-size="40" :right="false"></u-section>
		<!-- 包括：影院名称、地址、价格；点击一个影院进入选择场次页面。 -->
		<view class="yingyuan" v-for="(item,yingyuanid) in yingyuan" :key="yingyuanid" @click="tochoosechangci(yingyuanid)">
			<h3>影院名称:{{item.theatreName}}</h3>
			<text>地址:{{item.theatreName}}</text>
			<text>价格:{{item.price}}元</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				yingpian:'',
				yingyuan:[]
			}
		},
		methods: {
			tochoosechangci(id){
				uni.navigateTo({
					url:'choose_changci?movie_id='+this.id+'&yingyuan_name='+this.yingyuan[id].theatreName+'&yingyuan_id='+this.yingyuan[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/film/detail/'+this.id)
				this.yingpian=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/movie/theatre/times/list?movieId='+this.id)
				this.yingyuan=res2.rows
				console.log(res2);
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.moivetext{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.yingyuan{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
