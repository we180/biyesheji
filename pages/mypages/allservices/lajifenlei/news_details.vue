<template>
	<view>
		<view class="info">
			<!-- 详细页内显示标题，发布人，发布时间，正文。 -->
			<h3>{{newsinfo.title}}</h3>
			<h3>发布人:{{newsinfo.author}}</h3>
			<h3>发布时间:{{newsinfo.createTime}}</h3>
			<rich-text :nodes="newsinfo.content"></rich-text>
		</view>
		<u-gap></u-gap>
		<u-section title="评论" font-size="40" :right="false"></u-section>
		<u-gap></u-gap>
		<view class="comment">
			<u-input maxlength="30" border="border" type="textarea" style="margin: 14rpx;"></u-input>
			<u-button type="success" @click="submit">评论</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				newsinfo:''
			}
		},
		methods: {
			submit(){
				this.$u.toast('评论成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/garbage-classification/news/'+this.id)
				this.newsinfo=res1.data
				console.log(res1);
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	h3{
		text-align: center;
	}
</style>
