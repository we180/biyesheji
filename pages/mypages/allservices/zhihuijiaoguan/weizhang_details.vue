<template>
	<view>
		<!-- 违法时间、违法地点、违法行为、通知书号、违章记分、罚款金额。 -->
		<view class="info">
			<h3>违法时间:{{weizhang.badTime}}</h3>
			<h3>违法地点:{{weizhang.illegalSites}}</h3>
			<h3>违法行为:{{weizhang.trafficOffence}}</h3>
			<h3>通知书号:{{weizhang.noticeNo}}</h3>
			<h3>违章记分:{{weizhang.deductMarks}}分</h3>
			<h3>罚款金额:{{weizhang.money}}元</h3>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				weizhang:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/traffic/illegal/'+this.id)
				this.weizhang=res1.data
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
