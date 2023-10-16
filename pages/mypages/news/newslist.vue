<template>
	<view>
		<view class="newslist" v-for="(item,newsid) in news" :key="newsid" @click="tonews_De(newsid)">
			<!-- 图片、新闻标题、新闻内容缩写（多出的字用省略号显示）、评论总数、发布时间等信息 -->
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="230rpx" :src="baseUrl+item.cover"></u-image>
				</u-col>
				<u-col span="8">
					<h3 class="u-line-1">{{item.title}}</h3>
					<rich-text :nodes="item.content" class="u-line-4" style="height: 76px;"></rich-text>
					<view class="news_De">
						<text>评论总数:{{item.commentNum==null?'0':item.commentNum}}</text>
						<text>发布时间:{{item.publishDate}}</text>
					</view>
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				news:[]
			}
		},
		methods: {
			async getData(){
				let res5=await this.$u.get('/prod-api/press/press/list?title='+this.title)
				this.news=res5.rows
				console.log(res5);
			}
		},
		onLoad(ops) {
			this.title=ops.title
			this.getData()
		}
	}
</script>

<style scoped>
	.newslist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #888 2rpx solid;
	}
	.news_De{
		display: flex;
		justify-content: space-around;
		align-items: center;
		font-size: 27rpx;
	}
</style>
