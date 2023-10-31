<template>
	<view>
		<view class="head" style="text-align: center;">
			<u-tabs :list="orderstate" :current="current" @change="changetab"></u-tabs>
		</view>
		<!-- 上面显示店家类型 logo、店家名和订单状态（已完成、待支付、待评价）。中间显示购买信息，包括店家 logo、
		下单时间、总价格和支付方式等信息，点击中间项购买信息可跳转至订单详情页面。下面显示对应订单状态的操作按钮。 -->
		<view class="orderall" v-if="current==0">
			<view class="order" v-for="(item,orderlistid) in orderlist" :key="orderlistid">
				<view class="top">
					<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
					<h2>{{item.sellerInfo.name}}</h2>
					<h3>订单状态:{{item.orderInfo.status}}</h3>
				</view>
				<u-gap></u-gap>
				<view class="mid">
					<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
					<view class="u-flex-col u-m-l-10">
						<text>下单时间:{{item.orderInfo.createTime}}</text>
						<text>总价格:{{item.orderInfo.amount}}</text>
						<text v-if="item.orderInfo.paymentType">支付方式:{{item.orderInfo.paymentType}}</text>
					</view>
				</view>
				<u-gap></u-gap>
				<view class="bottom">
					<view class="" v-if="item.orderInfo.status=='待支付'">
						<u-button type="success" @click="tozhifu(orderlistid)">支付</u-button>
					</view>
					<view class="" v-if="item.orderInfo.status=='待评价'">
						<u-button type="success" @click="showcomment=true">评价</u-button>
						<u-popup v-model="showcomment" mode="bottom" class="popup">
							<u-gap></u-gap>
							<span> 评价星级:<u-rate :count="5" v-model="rate" size="45"></u-rate></span>
							<u-input type="textarea" border="border" style="padding: 16rpx;" v-model="content">
							</u-input>
							<u-button type="success" @click="comment(orderlistid)">评价</u-button>
						</u-popup>
						<u-button type="error" @click="showtuikuan=true">退款</u-button>
						<u-popup v-model="showtuikuan" mode="bottom">
							<u-gap></u-gap>
							<u-input type="textarea" border="border" placeholder="请输入退款理由" v-model="content_t">
							</u-input>
							<u-gap></u-gap>
							<u-button type="error" @click="tuikuan(orderlistid)">退款</u-button>
						</u-popup>
					</view>
					<view class="" v-if="item.orderInfo.status=='完成'">
						<u-button type="success" @click="tocomplete(orderlistid)">再来一单</u-button>
					</view>
					<view class="" v-if="item.orderInfo.status=='退款'">
						<h2 style="text-align: center;">已退款</h2>
					</view>
				</view>
			</view>
		</view>
		<view class="order_daizhifu" v-if="current==1">
			<view class="" v-for="(item,orderlistid) in orderlist" :key="orderlistid">
				<view class="order" v-if="item.orderInfo.status=='待支付'">
					<view class="top">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<h2>{{item.sellerInfo.name}}</h2>
						<h3>订单状态:{{item.orderInfo.status}}</h3>
					</view>
					<u-gap></u-gap>
					<view class="mid">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<view class="u-flex-col u-m-l-10">
							<text>下单时间:{{item.orderInfo.createTime}}</text>
							<text>总价格:{{item.orderInfo.amount}}</text>
							<text v-if="item.orderInfo.paymentType">支付方式:{{item.orderInfo.paymentType}}</text>
						</view>
					</view>
					<u-gap></u-gap>
					<view class="bottom">
						<view class="" v-if="item.orderInfo.status=='待支付'">
							<u-button type="success" @click="tozhifu(orderlistid)">支付</u-button>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="order_daizhifu" v-if="current==2">
			<view class="" v-for="(item,orderlistid) in orderlist" :key="orderlistid">
				<view class="order" v-if="item.orderInfo.status=='待评价'">
					<view class="top">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<h2>{{item.sellerInfo.name}}</h2>
						<h3>订单状态:{{item.orderInfo.status}}</h3>
					</view>
					<u-gap></u-gap>
					<view class="mid">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<view class="u-flex-col u-m-l-10">
							<text>下单时间:{{item.orderInfo.createTime}}</text>
							<text>总价格:{{item.orderInfo.amount}}</text>
							<text v-if="item.orderInfo.paymentType">支付方式:{{item.orderInfo.paymentType}}</text>
						</view>
					</view>
					<u-gap></u-gap>
					<view class="bottom">
						<view class="" v-if="item.orderInfo.status=='待评价'">
							<u-button type="success" @click="showcomment=true">评价</u-button>
							<u-popup v-model="showcomment" mode="bottom" class="popup">
								<u-gap></u-gap>
								<span> 评价星级:<u-rate :count="5" v-model="rate" size="45"></u-rate></span>
								<u-input type="textarea" border="border" style="padding: 16rpx;" v-model="content">
								</u-input>
								<u-button type="success" @click="comment(orderlistid)">评价</u-button>
							</u-popup>
							<u-button type="error" @click="showtuikuan=true">退款</u-button>
							<u-popup v-model="showtuikuan" mode="bottom">
								<u-gap></u-gap>
								<u-input type="textarea" border="border" placeholder="请输入退款理由" v-model="content_t">
								</u-input>
								<u-gap></u-gap>
								<u-button type="error" @click="tuikuan(orderlistid)">退款</u-button>
							</u-popup>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="order_daizhifu" v-if="current==3">
			<view class="" v-for="(item,orderlistid) in orderlist" :key="orderlistid">
				<view class="order" v-if="item.orderInfo.status=='退款'">
					<view class="top">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<h2>{{item.sellerInfo.name}}</h2>
						<h3>订单状态:{{item.orderInfo.status}}</h3>
					</view>
					<u-gap></u-gap>
					<view class="mid">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<view class="u-flex-col u-m-l-10">
							<text>下单时间:{{item.orderInfo.createTime}}</text>
							<text>总价格:{{item.orderInfo.amount}}</text>
							<text v-if="item.orderInfo.paymentType">支付方式:{{item.orderInfo.paymentType}}</text>
						</view>
					</view>
					<u-gap></u-gap>
					<view class="bottom">
						<view class="" v-if="item.orderInfo.status=='退款'">
							<h2 style="text-align: center;">已退款</h2>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="order_daizhifu" v-if="current==4">
			<view class="" v-for="(item,orderlistid) in orderlist" :key="orderlistid">
				<view class="order" v-if="item.orderInfo.status=='完成'">
					<view class="top">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<h2>{{item.sellerInfo.name}}</h2>
						<h3>订单状态:{{item.orderInfo.status}}</h3>
					</view>
					<u-gap></u-gap>
					<view class="mid">
						<u-image :src="baseUrl+item.sellerInfo.imgUrl" width="220" height="220"></u-image>
						<view class="u-flex-col u-m-l-10">
							<text>下单时间:{{item.orderInfo.createTime}}</text>
							<text>总价格:{{item.orderInfo.amount}}</text>
							<text v-if="item.orderInfo.paymentType">支付方式:{{item.orderInfo.paymentType}}</text>
						</view>
					</view>
					<u-gap></u-gap>
					<view class="bottom">
						<view class="" v-if="item.orderInfo.status=='完成'">
							<u-button type="success" @click="tocomplete(orderlistid)">再来一单</u-button>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				rate: 0,
				showtuikuan: false,
				showcomment: false,
				current: 0,
				orderstate: [{
						name: '全部'
					},
					{
						name: '待支付'
					},
					{
						name: '待评价'
					},
					{
						name: '退款'
					},
					{
						name: '完成'
					}
				],
				orderlist: [],
				content: '',
				content_t: ''
			}
		},
		methods: {
			tuikuan(id) {
				this.$u.post('/prod-api/api/takeout/order/refound', {
					orderNo:this.orderlist[id].orderInfo.orderNo,
					reason:this.content_t
				}).then(res => {
					console.log(res);
					this.$u.toast('退款成功')
					this.showtuikuan = false
					this.getData()
				})
			},
			comment(id) {
				this.$u.post('/prod-api/api/takeout/comment', {
					content: this.content,
					orderNo: this.orderlist[id].orderInfo.orderNo,
					score: this.rate
				}).then(res => {
					console.log(res);
					this.$u.toast('评论成功')
					this.showcomment = false
					this.getData()
				})
			},
			tocomplete(id) {
				uni.navigateTo({
					url: 'shop_details?id=' + this.orderlist[id].orderInfo.sellerId
				})
			},
			tozhifu(id) {
				uni.navigateTo({
					url: 'zhifu?total=' + this.orderlist[id].orderInfo.amount + '&orderNo=' + this.orderlist[id]
						.orderInfo.orderNo
				})
			},
			changetab(index) {
				this.current = index
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/takeout/order/list')
				this.orderlist = res1.rows
				console.log(res1);
			}
		},
		onShow() {
			this.getData()
		},
		onLoad() {
			if (this.vuex_token == '') {
				uni.redirectTo({
					url: '../login/login'
				})
			} else {
				this.getData()
			}
		}
	}
</script>

<style scoped>
	.top {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.mid {
		display: flex;
		flex-direction: row;
	}

	.order {
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
</style>
