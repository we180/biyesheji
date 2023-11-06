<template>
	<view>
		<view class="img">
			<image src="../../../../static/myimgs/myimg_dangjian/u=237204657,1833581701&fm=26&fmt=auto&gp=0.jpg" mode="" style="width: 100vw; height: 450rpx;"></image>
		</view>
		<view class="text">
			<h2>中华人民共和国驻摩洛哥王国大使馆党建</h2>
			<text>背景分析：
　　习近平总书记指出，要高度重视信息化发展对党的建设的影响，做到网络发展到哪里，党的工作就覆盖到哪里，充分运用信息技术改进党员教育管理、提高群众工作水平，加强网络舆论的正面引导。
　　人民日报评论：坚持以维护党中央权威为统领加强党对对外工作的集中统一领导。办好中国的事情，关键在党。我们要坚持外交大权在党中央，加强对外工作的集中统一领导和统筹协调，形成党总揽全局、协调各方的对外工作大协同局面。
　　为贯彻落实习近平总书记加强国有企业境外单位党的建设要求，为30余家驻摩洛哥中资企业、机构建立一个党建平台，将党建工作纳入统一管理，成为加强海外党建工作的有力抓手，2018年5月，在中国驻摩洛哥使馆李立大使的主导下，启动了驻摩洛哥使馆的海外党建云平台建设。
需求及方案：
　　2019年6月29日，中国驻摩洛哥使馆海外党建云平台成功启用。启用会上，李立大使表示：境外党建工作要适应境外单位的实际需要，客观上存在着两方面的距离：一是各单位和使馆的距离;二是各单位党员之间的距离。他强调，通过加强海外党建云平台的建设，有效解决了海外中资企业党员高度分散、不容易集中管理的难题，加强了中国驻摩中资机构30余家单位党组织和党员的管理，为海外党建插上信息化的“翅膀”。
　　该平台包括党建要闻、党建风采、党风廉政、学习园地、中摩合作、党务百科、通知公告、在线答题、服务信息九个栏目，为中国驻摩的中资机构党员提供及时有效的信息资讯、沟通交流和学习教育服务。
</text>
		</view>
		<view class="wrap">
			<view class="comment">
				<view class="top">
					<view class="left">
						<view class="heart-photo"><image :src="comment.url" mode=""></image></view>
						<view class="user-info">
							<view class="name">{{ comment.name }}</view>
							<view class="date">06-25 13:58</view>
						</view>
					</view>
					<view class="right" :class="{ highlight: comment.isLike }">
						{{ comment.likeNum }}
						<u-icon v-if="!comment.isLike" name="thumb-up" class="like" color="#9a9a9a" :size="30" @click="getLike"></u-icon>
						<u-icon v-if="comment.isLike" name="thumb-up-fill" class="like" :size="30" @click="getLike"></u-icon>
					</view>
				</view>
				<view class="content">{{ comment.contentText }}</view>
			</view>
			<view class="all-reply">
				<view class="all-reply-top">全部回复（{{ comment.allReply }}）</view>
				<view class="item">
					<view class="comment">
						<view class="top">
							<view class="left">
								<view class="heart-photo"><image :src="item.url" mode=""></image></view>
								<view class="user-info">
									<view class="name">{{ item.name }}</view>
									<view class="date">{{ item.date }}</view>
								</view>
							</view>
							<view class="right"  :class="{ highlight: item.isLike }">
								<view class="num">{{ item.likeNum }}</view>
								<u-icon v-if="!item.isLike" name="thumb-up" class="like" :size="30" color="#9a9a9a" @click="getLike(index)"></u-icon>
								<u-icon v-if="item.isLike" name="thumb-up-fill" class="like" :size="30" @click="getLike(index)"></u-icon>
							</view>
						</view>
						<view class="reply" v-if="item.reply">
							<view class="username">{{ item.reply.name }}</view>
							<view class="text">{{ item.reply.contentStr }}</view>
						</view>
						<view class="content">{{ item.contentText }}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			commentList: [],
			comment: ''
		};
	},
	onLoad() {
		this.getReply();
	},
	methods: {
		// 点赞
		getLike(index) {
			if (index === 0 || index > 0) {
				this.commentList[index].isLike = !this.commentList[index].isLike;
				if (this.commentList[index].isLike == true) {
					this.commentList[index].likeNum++;
				} else {
					this.commentList[index].likeNum--;
				}
			} else {
				if (this.comment.isLike == true) {
					this.comment.isLike = !this.comment.isLike;
					this.comment.likeNum--;
				} else {
					this.comment.isLike = !this.comment.isLike;
					this.comment.likeNum++;
				}
			}
		},

		// 回复列表
		getReply() {
			this.comment = {
				id: 1,
				name: '叶轻眉',
				date: '12-25 18:58',
				contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
				url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
				allReply: 12,
				likeNum: 33,
				isLikes: false
			};
			this.commentList = [
				{
					name: '新八几',
					date: '12-25 18:58',
					contentText: '不要乱打广告啊喂！虽然是真的超好用',
					url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
					likeNum: 33,
					isLike: false,
					reply: {
						name: 'uview',
						contentStr: 'uview是基于uniapp的一个UI框架，代码优美简洁，宇宙超级无敌彩虹旋转好用，用它！'
					}
				},
				{
					name: '叶轻眉1',
					date: '01-25 13:58',
					url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					allReply: 0,
					likeNum: 11,
					isLike: false,
					reply: {
						name: '粘粘',
						contentStr: '今天吃什么，明天吃什么，晚上吃什么，我只是一只小猫咪为什么要烦恼这么多'
					}
				},
				{
					name: '叶轻眉2',
					date: '03-25 13:58',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					allReply: 0,
					likeNum: 21,
					url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
					isLike: false,
					allReply: 2,
					reply: {
						name: '豆包',
						contentStr: '想吃冰糖葫芦粘豆包，但没钱5555.........'
					}
				},
				{
					name: '叶轻眉3',
					date: '06-20 13:58',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					allReply: 0,
					likeNum: 150,
					url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
					isLike: false
				}
			];
		}
	}
};
</script>

<style lang="scss" scoped>
page {
	background-color: #f2f2f2;
}
.comment {
	padding: 30rpx;
	font-size: 32rpx;
	background-color: #ffffff;
	.top {
		display: flex;
		justify-content: space-between;
	}
	.left {
		display: flex;
		.heart-photo {
			image {
				width: 64rpx;
				height: 64rpx;
				border-radius: 50%;
				background-color: #f2f2f2;
			}
		}
		.user-info {
			margin-left: 10rpx;
			.name {
				color: #5677fc;
				font-size: 28rpx;
				margin-bottom: 4rpx;
			}
			.date {
				font-size: 20rpx;
				color: $u-light-color;
			}
		}
	}
	.right {
		display: flex;
		font-size: 20rpx;
		align-items: center;
		color: #9a9a9a;
		.like {
			margin-left: 6rpx;
		}
		.num{
			font-size: 26rpx;
			color: #9a9a9a;
		}
	}
	.highlight {
		color: #5677fc;
		.num{
			color: #5677fc;
		}
	}
}
.all-reply {
	margin-top: 10rpx;
	padding-top: 20rpx;
	background-color: #ffffff;
	.all-reply-top {
		margin-left: 20rpx;
		padding-left: 20rpx;
		border-left: solid 4rpx #5677fc;
		font-size: 30rpx;
		font-weight: bold;
	}
	.item {
		border-bottom: solid 2rpx $u-border-color;
	}
	.reply {
		padding: 20rpx;
		background-color: rgb(242, 242, 242);
		border-radius: 12rpx;
		margin: 10rpx 0;
		.username {
			font-size: 24rpx;
			color: #7a7a7a;
		}
	}
}
</style>

