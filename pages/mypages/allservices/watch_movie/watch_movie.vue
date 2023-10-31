<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<view class="film" v-for="(item,filmid) in film" :key="filmid" @click="tofilm_de(filmid)">
			<!-- 图片、影片名称、上映时间、时长等内容 -->
			<u-image :src="baseUrl+item.cover" width="100%" height="300rpx"></u-image>
			<h2 style="text-align: center;">{{item.name}}</h2>
			<h3>上映时间:{{item.playDate}}</h3>
			<h3>时长:{{item.duration}}分钟</h3>
		</view>
		<u-gap></u-gap>
		<view class="lookmore">
			<u-button type="primary" @click="lookmore" v-if="showmore">查看更多</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showmore:true,
				banner:[],
				film:[],
				total:'',
				pageNum:1
			}
		},
		methods: {
			tofilm_de(id){
				uni.navigateTo({
					url:'movie_details?id='+this.film[id].id
				})
			},
			lookmore(){
				if(this.film.length<this.total){
					this.pageNum++
					this.getData()
				}else{
					this.$u.toast('没有更多了')
				}
			},
			search(index){
				this.$u.get('/prod-api/api/movie/film/list?name='+index).then(res=>{
					this.film=res.rows
					console.log(res);
					this.showmore=false
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/rotation/list')
				this.banner=res1.rows.map(res=>{
					return{
						image:this.baseUrl+res.advImg
					}
				})
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/movie/film/list?pageNum='+this.pageNum+'&pageSize=5')
				this.total=res2.total
				res2.rows.forEach(res=>{
					this.film.push(res)
				})
				console.log(res2);
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.film{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #AAAAAA;
		border-radius: 20rpx;
	}
</style>
