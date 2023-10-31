<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
<!-- 驿站地址，地址过长需换行，地址下面显示该驿站联系电话和提示办理入住时间段，入住时间下方显示男女显示剩余床位数。 -->
		<view class="yizhantest">
			<text>驿站地址:{{yizhan.address}}</text>
			<text>联系电话:{{yizhan.phone}}</text>
			<text>办理入住时间段:{{yizhan.workTime}}</text>
			<text>剩余床位(男):{{yizhan.bedsCountBoy}}</text>
			<text>剩余床位(女):{{yizhan.bedsCountGirl}}</text>
		</view>
		<u-gap></u-gap>
		<!-- 驿站简介、房间配置、周边配套和特色服务 -->
		<u-section title="驿站详细介绍" font-size="37" :right="false"></u-section>
		<view class="yizhantest">
			<text>驿站简介:{{yizhan.introduce}}</text>
			<text>房间配置:{{yizhan.internalFacilities}}</text>
			<text>周边配套:{{yizhan.surroundingFacilities}}</text>
			<text>特色服务:{{yizhan.specialService}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				yizhan:'',
				banner:[]
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/youth-inn/youth-inn/'+this.id)
				this.yizhan=res1.data
				console.log(res1);
				this.banner=this.yizhan.imageUrlList.map(res=>{
					return {
						image:this.baseUrl+res
					}
				})
				
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.yizhantest{
		margin: 10rpx;
		padding: 10rpx;
		display: flex;
		flex-direction: column;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
