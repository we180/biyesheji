<template>
	<view>
		<view class="phone">
			<u-section title="物业电话" font-size="40" :right="false"></u-section>
			<u-gap></u-gap>
			<u-cell-group>
				<u-cell-item icon="phone-fill" title="物业服务中心" value="1145141919" @click="callphone"></u-cell-item>
				<u-cell-item icon="phone-fill" title="停车位服务中心" value="1145141919" @click="callphone"></u-cell-item>
				<u-cell-item icon="phone-fill" title="24小时值班热线" value="1145141919" @click="callphone"></u-cell-item>
				<u-cell-item icon="phone-fill" title="报修电话" value="1145141919" @click="callphone"></u-cell-item>
				<u-cell-item icon="phone-fill" title="便民服务" value="1145141919" @click="callphone"></u-cell-item>
			</u-cell-group>
		</view>
		<view class="fankui">
			<u-button type="primary" @click="tofankui">我要反馈</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			callphone(){
				uni.makePhoneCall({
					phoneNumber:'1145141919'
				})
			},
			tofankui(){
				uni.navigateTo({
					url:'fankui'
				})
			},
		}
	}
</script>

<style scoped>

</style>
