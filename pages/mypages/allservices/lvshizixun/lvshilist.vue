<template>
	<view>
		<view class="choose">
			<u-dropdown>
				<u-dropdown-item title="排序方式" :options="paixu" v-model="value" @change="changevalue">
					
				</u-dropdown-item> 
				<u-dropdown-item title="筛选">
					<swiper :indicator-dots="true" :interval="3000" :duration="1000">
						<swiper-item >
							<view class="swiper-item" v-for="(item,typeid) in type.slice(0,8)" :key="typeid" @click="changelist(typeid)">
								<u-icon :name="baseUrl+item.imgUrl" size="66" label-pos="bottom" :label="item.name"></u-icon>
							</view>
						</swiper-item>
						<swiper-item >
							<view class="swiper-item" v-for="(item,typeid) in type.slice(8,16)" :key="typeid+8" @click="changelist(typeid+8)">
								<u-icon :name="baseUrl+item.imgUrl" size="66" label-pos="bottom" :label="item.name"></u-icon>
							</view>
						</swiper-item>
					</swiper>
				</u-dropdown-item>
			</u-dropdown>
		</view>
		<view class="lvshilist" v-for="(item,lvshilistid) in lvshilist" :key="lvshilistid">
			<u-row @click="tolvshi_De(lvshilistid)">
				<u-col span="4">
					<u-image width="100%" height="250rpx" :src="baseUrl+item.avatarUrl"></u-image> 
				</u-col>
				<u-col span="8" style="display: flex;flex-direction: column;" align="top">
					<text>{{item.name}}</text>
					<text>从业年限:{{item.workStartAt}}</text>
					<text>咨询人数:{{item.serviceTimes}}</text>
					<text>法律专长:{{item.legalExpertiseName}}</text>
					<text>好评率:{{item.favorableRate}}</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-button type="success" @click="tozixun">咨询</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				name:'',
				lvshilist:[],
				value:0,
				paixu:[
					{
						label:'默认排序',
						value:0
					},
					{
						label:'从业年限',
						value:1
					},
					{
						label:'服务人数',
						value:2
					},
					{
						label:'好评率',
						value:3
					},
				],
				type:[]
			}
		},
		methods: {
			changevalue(id){
				if(id==0){
					this.getData()
				}else if(id==1){
					this.lvshilist=this.lvshilist.sort((a,b)=>{
						return this.nianXian(b.workStartAt) - this.nianXian(a.workStartAt)
					})
				}else if(id==2){
					this.lvshilist=this.lvshilist.sort((a,b)=>{
						return b.serviceTimes-a.serviceTimes
					})
				}else if(id==3){
					this.lvshilist=this.lvshilist.sort((a,b)=>{
						return a.favorableRate-b.favorableRate
					})
				}
			},
			nianXian(e){
				return 2023 - new Date(e).getFullYear()
			},
			changelist(id){
				this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list?legalExpertiseId='+this.type[id].id).then(res=>{
					console.log(res);
					this.lvshilist=res.rows
				})
			},
			tolvshi_De(id){
				uni.navigateTo({
					url:'lvshi_details?id='+this.lvshilist[id].id
				})
			},
			async getData(){
				if(this.name){
					let res3=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list?name='+this.name)
					this.lvshilist=res3.rows
					console.log(res3);
				}else{
					let res1=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list')
					this.lvshilist=res1.rows
					console.log(res1);
				}
				if(this.id){
					let res4=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list?legalExpertiseId='+this.id)
					this.lvshilist=res4.rows
					console.log(res4);
				}else{
					let res1=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list')
					this.lvshilist=res1.rows
					console.log(res1);
				}
				
				let res2=await this.$u.get('/prod-api/api/lawyer-consultation/legal-expertise/list')
				this.type=res2.rows.sort((a,b)=>{
					return b.sort-a.sort
				})
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.name=ops.name
			this.getData()
		}
	}
</script>

<style scoped>
	.lvshilist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	swiper-item{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		background-color: #fff;
	}
	.swiper-item{
		width: 25%;
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
