<template>
	<view>
		<!-- 对方信息（包括车牌号）、本人信息（包括姓名、手机号、身份证号） -->
		<view class="input">
			<u-field label="车牌号"></u-field>
			<u-field label="姓名"></u-field>
			<u-field label="手机号"></u-field>
			<u-field label="身份证号"></u-field>
		</view>
		<view class="u-demo">
			<view class="u-demo-wrap">
				<view class="u-demo-title">城市选择</view>
				<view class="u-demo-area">
					<city-select v-model="value" @city-change="cityChange"></city-select>
					<view class="u-demo-result-line">{{ input ? input : '选择的城市' }}</view>
				</view>
			</view>
			<view class="u-config-wrap">
				<view class="u-config-item">
					<u-button @click="value = true">打开城市列表</u-button>
				</view>
			</view>
		</view>
		<u-section title="挪车现场照片" font-size="40" :right="false"></u-section>
		<u-upload :action="action"></u-upload>
		<u-button type="success" @click="show=1">提交</u-button>
		<!-- 车主电话号码，对话框显示车牌和车主电话，点击电话号码直接拨号。 -->
		<view class="back" v-if="show" @click="callphone">
			<h3>车牌:辽B12345</h3>
			<h3>车主电话:13800000000</h3>
		</view>
	</view>
</template>

<script>
	import citySelect from '../../../../template/citySelect/u-city-select.vue';
	export default {
		components: {
			citySelect
		},
		data() {
			return {
				show:0,
				action:'http://192.168.1.105:10001/prod-api/common/upload',
				height: 30,
				bgColor: this.$u.color.bgColor,
				marginTop: 30,
				marginBottom: 30,
				value: false,
				input: '',
			};
		},
		
		methods: {
			callphone(){
				uni.makePhoneCall({
					phoneNumber: '13800000000'
				});
			},
			cityChange(e) {
				this.input = e.province.label + '-' + e.city.label + '-' + e.area.label;
			}
		}
	};
</script>

<style scoped>
	.btn-wrap {
		margin: 100rpx 30rpx;
	}
	.back{
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		margin: 10rpx;
	}
</style>
