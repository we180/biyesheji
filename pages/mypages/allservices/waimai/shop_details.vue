<template>
	<!-- 店家封面、店名、评分、月销量、人均消费、收藏图标， -->
	<view>
		<view class="shopinfo">
			<image :src="baseUrl+shopinfo.imgUrl" mode=""></image>
			<view class="shoptext">
				<h3>{{shopinfo.name}}</h3>
				<text>评分:{{shopinfo.score}}</text>
				<text>月销量:{{shopinfo.saleQuantity}}</text>
				<text>人均消费:{{shopinfo.avgCost}}</text>
				<u-icon @click="likestate" :label="likeflag==false?'收藏':'已收藏'"
					:name="likeflag==false?'star':'star-fill'" size="60"></u-icon>
			</view>
		</view>
		<view class="bottom">
			<u-tabs :list="tabs" :current="current" @change="changetab" style="text-align: center;"></u-tabs>
			<view class="diancai" v-if="current==0" style="display: flex;">
				<scroll-view scroll-y="true" style="flex: 1;">
					<view v-for="(item,typelist) in typelist" :key="typelist" class="type"
						@click="changefood(typelist,item.id)">
						{{item.name}}
					</view>
				</scroll-view>
				<scroll-view scroll-y="true" style="flex: 3;height: 600rpx;" class="foodlist">
					<!-- 菜图片、菜名、月销量、好评率、价格以及+图标 -->
					<view v-for="(item,foodid) in food" :key="foodid" class="food">
						<u-row>
							<u-col span="4">
								<image :src="baseUrl+item.imgUrl" mode=""></image>
							</u-col>
							<u-col span="8" style="display: flex;flex-direction: column;">
								<h3>{{item.name}}</h3>
								<text>月销量:{{item.saleQuantity}}</text>
								<text>好评率:{{item.favorRate}}</text>
								<text>价格:{{item.price}}</text>
								<view class="foondnum">
									<u-icon name="plus" size="50" @click="add(item,foodid)"></u-icon>
									<text>{{item.num||0}}</text>
									<u-icon name="minus" size="50" @click="cancle(item,foodid)"></u-icon>
								</view>
							</u-col>
						</u-row>
					</view>
					<u-gap></u-gap>
					<u-gap></u-gap>
					<u-gap></u-gap>
					<u-gap></u-gap>
				</scroll-view>
			</view>
			<view class="total">
				<view class="total_left">
					<h3>菜品数量:{{total()}}</h3>
					<h3>总价:{{money()}}</h3>
				</view>
				<view class="total_right" @click="dingdanqueren">
					<h2>去结算</h2>
				</view>
			</view>
			<view class="pingjia" v-if="current==1">
				<!-- 用户头像、用户昵称、评分值（5 角星标识）、评论内容和评论时间，以及商家回复。 -->
				<view style="text-align: center;">
					店家综合评分:<u-rate :count="5" v-model="shopinfo.score" :disabled="true"></u-rate>
				</view>
				<view class="usercomment">
					<view class="comment" v-for="(item,commentlist) in commentlist" :key="commentlist">
						<view class="userimg">
							<image :src="baseUrl+'/prod-api'+item.avatar" mode=""></image>
							<h3 style="text-align: center;">{{item.userName}}</h3>
						</view>
						<view class="usertext">
							<text>评分值:</text>
							<u-rate :count="5" v-model="item.score" :disabled="true"></u-rate>
							<text>{{item.content}}</text>
							<text>评论时间:{{item.commentDate}}</text>
							<text v-if="item.replyContent!==null">商家回复:{{item.replyContent}}</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import classifyData from "@/common/classify.data.js";
	export default {
		data() {
			return {
				current: 0,

				id: '',
				shopinfo: '',
				likeflag: '',
				tabs: [{
						name: '点菜'
					},
					{
						name: '评价'
					},
					{
						name: '商家介绍'
					}
				],
				commentlist: [],
				typelist: [],
				food: [],
				gouwuche: []
			}
		},
		methods: {
			dingdanqueren(){
				uni.navigateTo({
					url:'dingdan_queren?foodlist='+JSON.stringify(this.gouwuche)+'&name='+this.shopinfo.name
				})
				
			},
			add(item, id) {
				if (this.food[id].num) {
					this.food[id].num++
				} else {
					this.food[id].num = 1
				}
				let flag = true;
				for (let i = 0; i < this.gouwuche.length; i++) {
					if (this.gouwuche[i].id == this.food[id].id) {
						flag = false
						this.gouwuche[i].num = this.food[id].num
						break
					}
				}
				if (flag) {
					this.gouwuche.push(item)
				}
				this.$forceUpdate()
			},
			cancle(item, id) {
				if(this.food[id].num>0){
					this.food[id].num--
					for (let i = 0; i < this.gouwuche.length; i++) {
						if (this.gouwuche[i].id == this.food[id].id) {
							this.gouwuche[i].num = this.food[id].num
							if (this.gouwuche[i].num == 0) {
								this.gouwuche.splice(i)
							}
							break
						}
					}
				}else{
					
				}
				
				this.$forceUpdate()
			},
			total(){
				let sum=0;
				this.gouwuche.forEach(res=>{
					sum+=res.num
				})
				return sum
			},
			money(){
				let sum=0;
				this.gouwuche.forEach(res=>{
					sum+=res.num*res.price
				})
				return sum.toFixed(2)
			},
			async changefood(item,id) {
				let res4=await this.$u.get('/prod-api/api/takeout/product/list', {
					categoryId: this.typelist[item].id,
					sellerId: this.id
				})
				this.gouwuche.forEach(res=>{
					res4.data.forEach(res1=>{
						if(res.id==res1.id){
							res1.num=res.num
						}
					})
				})
				this.food=res4.data
			},
			changetab(index) {
				this.current = index
			},
			_likeflag() {
				this.$u.get('/prod-api/api/takeout/collect/check?sellerId=' + this.id).then((res) => {
					this.likeflag = res.isCollect
				})
			},
			likestate() {
				if (this.likeflag == false) {
					this.$u.post('/prod-api/api/takeout/collect', {
						sellerId: this.id
					}).then((res) => {
						console.log(res);
						console.log('+++');
						this._likeflag()
					})
				} else {
					this.$u.delete('/prod-api/api/takeout/collect/' + this.id).then((res) => {
						console.log(res);
						this._likeflag()
					})
				}
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/takeout/seller/' + this.id)
				this.shopinfo = res1.data
				// console.log(res1);
				let res2 = await this.$u.get('/prod-api/api/takeout/comment/list?sellerId=' + this.id)
				this.commentlist = res2.rows
				// console.log(res2);
				let res3 = await this.$u.get('/prod-api/api/takeout/category/list?sellerId=' + this.id)
				this.typelist = res3.data
				console.log(res3);
				let res4 = await this.$u.get('/prod-api/api/takeout/product/list', {
					categoryId: this.typelist[0].id,
					sellerId: this.id
				})
				this.food = res4.data
			}
		},
		onLoad(options) {
			this.id = options.id
			this.getData()
			this._likeflag()
		}
	}
</script>

<style scoped>
	.shopinfo {
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}

	.shopinfo image {
		width: 100%;
	}

	.shoptext {
		display: flex;
		flex-direction: column;
	}

	.userimg image {
		width: 100rpx;
		height: 100rpx;
	}

	.comment {
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}

	.usertext {
		display: flex;
		flex-direction: column;
		margin-left: 10rpx;

	}

	.type {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 80rpx;
		background-color: #ccc;
	}

	.foodlist image {
		width: 100%;
		height: 160rpx;
	}

	.food {
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}

	.foondnum {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		width: 100%;
	}

	.total {
		width: 80vw;
		height: 8vh;
		background-color: #A0CFFF;
		border-radius: 30rpx;
		position: fixed;
		bottom: 20rpx;
		right: 80rpx;
		display: flex;
	}

	.total_right {
		border-radius: 30rpx;
	}

	.total_left {
		flex: 2;
		display: flex;
		flex-direction: row;
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		height: 100%;
	}

	.total_right {
		height: 100%;
		flex: 1;
		background-color: #ccc;
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
