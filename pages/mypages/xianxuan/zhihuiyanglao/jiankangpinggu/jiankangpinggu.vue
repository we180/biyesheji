<template>
	<view>
		<view class="head">
			<u-section :font-size="40" title="选择成员" sub-title="新增成员"></u-section>
			<view class="human">
				<u-row>
					<u-col span="3">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/pionner2.png" width="100%" height="200rpx"
							mode="aspectFit"></u-image>
					</u-col>
					<u-col span="7">
						<view class="text" style="display: flex;flex-direction: column;">
							<h2>小红</h2>
							<text>性别:女</text>
							<text>年龄:51</text>
						</view>
					</u-col>
					<u-col span="2">
						<u-button type="warning">删除</u-button>
					</u-col>
				</u-row>
			</view>
		</view>
		<u-gap></u-gap>
		<view class="state">
			<u-section :font-size="40" title="请选择健康状态" :right="false"></u-section>
<!-- 精神状态（正常、痴呆、抑郁、暴力），活动能力（正常，拄拐、轮椅、卧床），生活自理能力（饮食、洗澡、穿衣、修饰） -->
			<u-field label="精神状态" v-model="jingshen" @click="showjingshen=true" input-align="right" placeholder="请输入"></u-field>
			<u-action-sheet :list="jingshenlist" v-model="showjingshen" @click="click1"></u-action-sheet> 
			<u-field label="活动能力" v-model="huodong" @click="showhuodong=true" input-align="right" placeholder="请输入"></u-field>
			<u-action-sheet :list="huodonglist" v-model="showhuodong" @click="click2"></u-action-sheet>
			<u-field label="生活自理能力" v-model="zili" @click="showzili=true" input-align="right" placeholder="请输入"></u-field>
			<u-action-sheet :list="zililist" v-model="showzili" @click="click3"></u-action-sheet>
		</view>
		<view class="pinggu">
			<u-button type="primary" @click="topinggu">评估</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showjingshen:false,
				showhuodong:false,
				showzili:false,
				jingshen:'',
				huodong:'',
				zili:'',
				jingshenlist:[
					{
						text:'正常'
					},
					{
						text:'痴呆'
					},
					{
						text:'抑郁'
					},
					{
						text:'暴力'
					},
				],
				huodonglist:[
					{
						text:'正常'
					},
					{
						text:'拄拐'
					},
					{
						text:'轮椅'
					},
					{
						text:'卧床'
					},
				],
				zililist:[
					{
						text:'饮食'
					},
					{
						text:'洗澡'
					},
					{
						text:'穿衣'
					},
					{
						text:'修饰'
					},
				],
			}
		},
		methods: {
			topinggu(){
				uni.navigateTo({
					url:'pinggu_res'
				})
			},
			click1(index){
				if(index==0){
					this.jingshen='正常'
				}else if(index==1){
					this.jingshen='痴呆'
				}else if(index==2){
					this.jingshen='抑郁'
				}else if(index==3){
					this.jingshen='暴力'
				}
				
			},
			click2(index){
				if(index==0){
					this.huodong='正常'
				}else if(index==1){
					this.huodong='拄拐'
				}else if(index==2){
					this.huodong='轮椅'
				}else if(index==3){
					this.huodong='卧床'
				}
			},
			click3(index){
				if(index==0){
					this.zili='饮食'
				}else if(index==1){
					this.zili='洗澡'
				}else if(index==2){
					this.zili='穿衣'
				}else if(index==3){
					this.zili='修饰'
				}
			},
		}
	}
</script>

<style scoped>
	.human{
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 4rpx solid;
		border-radius: 20rpx;
	}
</style>
