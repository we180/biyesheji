<template>
	<view>
		<u-section :right="false" font-size="40" title="宠物种类"></u-section>
		<view class="type">
			<view class="typelist" v-for="(item,typeid) in type" :key="typeid" @click="tofind_doc(typeid)">
				<u-icon :name="baseUrl+item.imgUrl" :label="item.name" size="60" label-pos="bottom"></u-icon>
			</view>
		</view>
		<u-gap></u-gap>
		<u-section :right="false" font-size="40" title="我的问诊列表"></u-section>
		<view class="explistall">
			<view class="explist" v-for="(item,mylistid) in mylist" :key="mylistid" @click="towenzhen_de(item)">
				<view class="docimg">
					<image :src="baseUrl+item.doctor.avatar" mode=""></image>
					<h3 style="text-align: center;">{{item.doctor.name}}</h3>
				</view>
				<view class="exptext">
					<text>案例描述:{{item.question}}</text>
				</view>
			</view>
		</view>
		<u-section :right="false" font-size="40" title="问诊案例列表"></u-section>
		<view class="explistall">
			<view class="explist" v-for="(item,explistid) in explist" :key="explistid" @click="toexp_de(item)">
				<view class="docimg">
					<image :src="baseUrl+item.doctor.avatar" mode=""></image>
					<h3 style="text-align: center;">{{item.doctor.name}}</h3>
				</view>
				<view class="exptext">
					<text>案例描述:{{item.question}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type:[],
				mylist:[],
				explist:[]
			}
		},
		methods: {
			toexp_de(item){
				uni.navigateTo({
					url:'exp_details?item='+JSON.stringify(item)
				})
			},
			towenzhen_de(item){
				uni.navigateTo({
					url:'wenzhen_details?item='+JSON.stringify(item)
				})
			},
			tofind_doc(id){
				uni.navigateTo({
					url:'find_doc?id='+this.type[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/pet-hospital/pet-type/list')
				this.type=res1.data
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/pet-hospital/inquiry/my-list')
				this.mylist=res2.rows
				// console.log(res2);
				let res3=await this.$u.get('/prod-api/api/pet-hospital/inquiry/list')
				this.explist=res3.rows
				// console.log(res3);
			}
		},
		onShow() {
			this.getData()
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.typelist{
		display: flex;
		width: 20%;
		justify-content: center;
		align-items: center;
		margin-top: 10rpx;
	}
	.docimg image{
		width: 230rpx;
		height: 230rpx;
	}
	.explist{
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF solid 2rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
	}
	.exptext{
		margin-left: 10rpx;
	}
</style>
