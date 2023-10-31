<template>
	<view>
		<!-- 影封面图片、电影名称、评分、上映时间、想看人数等信息 -->
		<view class="info">
			<u-image :src="baseUrl+film.cover" width="100%" height="300rpx"></u-image>
			<h2 style="text-align: center;">{{film.name}}</h2>
			<h3>评分:{{film.score}}</h3>
			<h3>上映时间:{{film.playDate}}</h3>
			<h3>想看人数:{{film.likeNum}}</h3>
		</view>

		<view class="back">
			<u-button type="success" @click="back">主页</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id: '',
				film: ''
			}
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/movie/film/detail/' + this.id)
				this.film = res1.data
				console.log(res1);
			},
		},
		onLoad(ops) {
			this.id = ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.back {
		position: fixed;
		bottom: 20rpx;
		width: 90%;
		right: 5%;
	}
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #AAAAAA;
		border-radius: 20rpx;
	}
</style>
