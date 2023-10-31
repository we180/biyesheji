<template>
	<view>
		<view class="input">
			<u-field label="收货地址" v-model="address" @click="showaddress=true" :disabled="true"></u-field>
			<u-popup v-model="showaddress" mode="bottom">
				<view class="addresslist">
					<view class="address" v-for="(item,addressallid) in addressall" :key="addressallid" @click="chooseaddress(addressallid)">
						<text>{{item.addressDetail}}</text>
						<text>详细地址:{{item.label}}</text>
						<text>联系人:{{item.name}}</text>
						<text>电话:{{item.phone}}</text>
					</view>
				</view>
			</u-popup>
		</view>
		<view class="choosed">
			<!-- 上方显示店家名，下方显示选中的菜品列表 -->
			<!-- 菜品信息布局为左侧菜品封面，中间上方显示菜品名称，中间下方购买数量，右侧显示价格。 -->
			<view class="title">
				<h2 style="text-align: center; ">{{name}}</h2>
			</view>
			<view class="foodlist">
				<view class="food" v-for="(item,foodlistid) in foodlist" :key="foodlistid">
					<u-row>
						<u-col span="3">
							<u-image :src="baseUrl+item.imgUrl" width="180rpx" height="180rpx"></u-image>
						</u-col>
						<u-col span="6" class="foodindex">
							<text>{{item.name}}</text>
							<text>购买数量:{{item.num}}</text>
						</u-col>
						<u-col span="3">
							<h4>总计:{{item.price*item.num}}</h4>
						</u-col> 
					</u-row>
				</view>
			</view>
		</view>
		<view class="updingdan">
			<u-button type="success" @click="updingdan">提交订单</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showaddress: false,
				address: '',
				addressall: [],
				foodlist:[],
				addressDetail:'',
				name:'',
				total:0,
				orderItemList:[]
			}
		},
		methods: {
			updingdan(){
				this.$u.post('/prod-api/api/takeout/order/create',{
					addressDetail:this.addressDetail.addressDetail,
					label:this.addressDetail.label,
					name:this.addressDetail.name,
					phone:this.addressDetail.phone,
					amount:this.total,
					orderItemList:this.orderItemList,
					sellerId:this.foodlist[0].sellerId
				}).then(res=>{
					console.log(res);
					uni.navigateTo({
						url:'zhifu?total='+this.total+'&orderNo='+res.orderNo
					})
				})
			},
			chooseaddress(id){
				this.address=this.addressall[id].label+'  '+this.addressall[id].addressDetail
				this.addressDetail=this.addressall[id]
				this.showaddress=false
				console.log(this.addressDetail);
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/takeout/address/list')
				this.addressall = res1.data
				console.log(res1);
			}
		},
		onLoad(options) {
			this.name=options.name
			this.foodlist=JSON.parse(options.foodlist)
			console.log(this.foodlist);
			this.foodlist.forEach(res=>{
				this.total+=res.num*res.price
			})
			// console.log(this.total);
			for (let i = 0; i < this.foodlist.length; i++) {
				let temp={
					productId:this.foodlist[i].id,
					quantity:this.foodlist[i].num
				}
				this.orderItemList.push(temp)
			}
			this.getData()
		}
	}
</script>

<style scoped>
	.address {
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
	.food image{
		width: 180rpx;
		height: 180rpx;
	}
	.foodindex{
		display: flex;
		flex-direction: column;
	}
</style>
