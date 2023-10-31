<template>
	<view>
		<view class="head">
			<u-navbar back-text="返回" title="地址管理">
				<u-icon name="home" label="新增地址" size="50" slot="right" style="margin-right: 10rpx;"
					@click="showinputM"></u-icon>
			</u-navbar>
		</view>
		<view class="addresslist">
			<view class="address" v-for="(item,addresslistid) in addresslist" :key="addresslistid">
				<u-row>
					<u-col span="10">
						<view class="addressindex">
							<h3>收货地址:{{item.addressDetail}}   {{item.label}}</h3>
							<text>联系人:{{item.name}}</text>
							<text>联系电话:{{item.phone}}</text>
						</view>
					</u-col>
					<u-col span="2">
						<view class="changeaddress">
							<u-button type="primary" @click="changeaddressM">编辑</u-button>
							<u-popup v-model="changeinput" mode="bottom" height="800">
								<u-field label="省市区:" v-model="address" @click="changeaddress=true"></u-field>
								<u-field label="详细地址" v-model="address_de"></u-field>
								<u-field label="联系人" v-model="name"></u-field>
								<u-field label="手机号" v-model="phone"></u-field>
								<u-button type="success" @click="change_saveaddress(addresslistid)">保存地址</u-button>
								<u-button type="error" @click="deleteaddress(addresslistid)">删除地址</u-button>
								<u-picker v-model="changeaddress" mode="region" @confirm="inputaddress"></u-picker>
							</u-popup>
						</view>
					</u-col>
				</u-row>
				
				
			</view>
		</view>
		<view class="newaddress">
			<u-popup v-model="showinput" mode="bottom" height="800">
				<u-field label="省市区:" v-model="address" @click="showaddress=true"></u-field>
				<u-field label="详细地址" v-model="address_de"></u-field>
				<u-field label="联系人" v-model="name"></u-field>
				<u-field label="手机号" v-model="phone"></u-field>
				<u-button type="success" @click="saveaddress">保存地址</u-button>
				<u-picker v-model="showaddress" mode="region" @confirm="inputaddress"></u-picker>
			</u-popup>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showinput: false,
				showaddress: false,
				address_de: '',
				name: '',
				phone: '',
				address: '',
				addresslist: [],
				changeinput:false,
				changeaddress:false

			}
		},
		methods: {
			deleteaddress(id){
				this.$u.delete('/prod-api/api/takeout/address/'+this.addresslist[id].id).then(res=>{
					console.log(res);
					this.$u.toast('删除成功')
					this.changeinput=false
					this.getData()
				})
			},
			change_saveaddress(id){
				this.$u.put('/prod-api/api/takeout/address',{
					id:this.addresslist[id].id,
					addressDetail: this.address,
					label: this.address_de,
					name: this.name,
					phone: this.phone
				}).then(res=>{
					console.log(res);
					this.changeinput = false
				})
				this.getData()
				this.$forceUpdate()
			},
			changeaddressM(){
				this.changeinput=true
				this.$u.get('/prod-api/api/common/user/getInfo').then(res=>{
					this.name=res.user.nickName
					this.phone=res.user.phonenumber
				})
			},
			showinputM(){
				this.showinput=true
				this.$u.get('/prod-api/api/common/user/getInfo').then(res=>{
					this.name=res.user.nickName
					this.phone=res.user.phonenumber
				})
			},
			inputaddress(item) {
				this.address = item.province.label + item.city.label + item.area.label
			},
			saveaddress() {
				this.$u.post('/prod-api/api/takeout/address', {
					addressDetail: this.address,
					label: this.address_de,
					name: this.name,
					phone: this.phone
				}).then(res => {
					console.log(res);
					this.showinput = false
				})
				this.getData()
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/takeout/address/list')
				this.addresslist = res1.data
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.address{
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
	.addressindex{
		display: flex;
		flex-direction: column;
	}
</style>
