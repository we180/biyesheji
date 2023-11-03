<template>
	<view>
		<!-- 标题、发布者、图片、内容、发布日期、查看人数、点赞人数，点击“点赞”按钮可为该扶贫案例点赞 -->
		<h2 style="text-align: center;">走进精准扶贫“首倡地”——湖南湘西十八洞村</h2>
		<u-gap></u-gap>
		<h3 style="text-align: center;">下北泽村委会</h3>
		<h3 style="text-align: center;">2022/12/10</h3>
		<u-image src="../../../../../static/myimgs/myimg_fupin/368cab1c600c364ef27d27c6e1bc0656@2x.png" width="100%" height="300rpx" border-radius="20rpx"></u-image>
		<view class="text">
			<text>
				“决战决胜2020——走进‘精准扶贫’首倡地”，近日，《先锋》作为全国党刊全媒体采访团一员，来到湘西州十八洞村，聚焦精准扶贫的湘西经验，挖掘湘西州精准扶贫故事，近距离感受“首倡之地”的发展变化。十八洞村地处中国武陵山脉腹地，是一个藏在偏僻幽静山谷中的苗族聚居贫困村。过去，因为基础设施差、闭塞落后，外村女子不愿嫁入，村里鲜有陌生面孔。到2013年，全村贫困发生率高达57%，集体经济空白。2013年11月3日，习近平总书记在湖南湘西十八洞村视察时首次提出“精准扶贫”重要论述。经过7年的努力，目前十八洞村的贫困发生率已降至“0”，贫困人口全部脱贫。2016年，全村人均纯收入达到8313元。2017年2月，经湖南省人民政府审核批准，十八洞村成功脱贫出列。2019年，全村人均纯收入由2013年的1668元增加到14668元，130户521名贫困人口全部实现脱贫，贫困发生率由2013年的56.76%下降到0，村集体经济收入达126.4万元，基础设施和公共服务不断完善，全村实现了稳定脱贫，正在向乡村振兴的路上大步前进。这一切的改变，源于精准扶贫。湘西，是习近平总书记精准扶贫重要论述的首倡地。这一场“劲风”，从十八洞村吹来，拂遍湘西大地。
			</text>
			<h3>查看人数:114514</h3>
			<h3>点赞人数:{{likecount}}</h3>
			<u-button type="success" @click="like" :disabled="likestate">{{liketext}}</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				likecount:9876,
				liketext:"点赞",
				likestate:false
			}
		},
		methods: {
			like(){
				this.$u.toast('点赞成功!')
				this.likecount++
				this.liketext="已点赞"
				this.likestate=true
				this.$forceUpdate()
			}
		}
		
	}
</script>

<style scoped>
	.text{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #ccc 4rpx solid;
	}
</style>
