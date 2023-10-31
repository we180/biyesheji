<template>
	<view>
		<!-- 医生头像、医生姓名、医生职称、执业编号、咨询描述、图片、问答列表、追问输入框和发送按钮 -->
		<view class="docinfo">
			<view class="docimg">
				<image :src="baseUrl+item.doctor.avatar" mode=""></image>

			</view>
			<h3 style="text-align: center;">{{item.doctor.name}}</h3>
			<view class="doctext">

				<text>医生职称:{{item.doctor.jobName}}</text>
				<text>执业编号:{{item.doctor.practiceNo}}</text>
				<text>咨询描述:{{item.question}}</text>
				<image :src="baseUrl+'/prod-api'+item.imageUrls" mode=""></image>
			</view>
		</view>
		<h3 style="text-align: center;">问答列表</h3>
		<view class="wenda">
			<view class="wendalist" v-for="(item,wendaid) in wenda" :key="wendaid">
				<h4>用户ID:{{item.fromId}}</h4>
				<text>{{item.content}}</text>
			</view>
		</view>
		<view class="zhuiwen">
			<h3 style="text-align: center;">追问医生</h3>
			<view class="input">
				<u-input v-model="content" height="300" border="border" type="textarea"></u-input>
			</view>
			<u-button type="success" @click="send">发送</u-button>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				item: {},
				wenda: [],
				content: ''
			}
		},
		methods: {
			send() {
				this.$u.post('/prod-api/api/pet-hospital/inquiry-message', {
					inquiryId: this.item.id,
					content: this.content
				}).then((res) => {
					console.log(res);
					this.getData()
					this.content = ''
				})
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/pet-hospital/inquiry-message/list?inquiryId=' + this.item
					.id)
				this.wenda = res1.rows
				console.log(res1);
			}
		},
		onLoad(options) {
			this.item = JSON.parse(options.item)
			console.log(this.item);
			this.getData()
		}
	}
</script>

<style scoped>
	.doctext {
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF solid 2rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
	}

	.docimg image {
		width: 100%;
	}

	.wendalist {
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF solid 2rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
	}
</style>
