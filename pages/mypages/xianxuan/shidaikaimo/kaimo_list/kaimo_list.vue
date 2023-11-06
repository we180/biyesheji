<template>
	<view>
		<view class="kaimolist">
			<view class="kaimo" @click="tokaimo_De">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/W020211011361082030178.png" width="100%"
							height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>楷模介绍</h3>
						<text class="u-line-5">孙景坤在革命战争年代冲锋陷阵、不怕牺牲。在解放战争中，他先后参加四平战役、辽沈战役、平津战役、解放长沙战役和解放海南岛战役，荣立二等功两次、三等功一次，被授予解放东北纪念章、解放华北纪念章、解放华中南纪念章和解放海南岛纪念章</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/1.png" width="100%"
							height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>楷模介绍</h3>
						<text class="u-line-5">杜富国是陆军某扫雷排爆大队战士。入伍以来，他始终把忠诚和信仰刻在心中，把使命和责任扛在肩上，主动请缨征战雷场，苦练精练过硬本领，为人民利益和边境安宁挥洒热血，在平凡岗位干出了突出业绩。2018年10月11日，杜富国随队参加排雷作业时，危急时刻冲锋在前，为保护战友身受重伤，失去双眼和双手。杜富国同志曾先后获得“全国自强模范”“感动中国十大人物”、陆军“四有”新时代革命军人标兵等称号，荣立个人一等功。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/2.png" width="100%"
							height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>楷模介绍</h3>
						<text class="u-line-5">毛相林，男，汉族，1959年1月出生，初中文化，中共党员，重庆市巫山县竹贤乡下庄村党支部书记、村委会主任。1997年，担任老下庄村支书的毛相林带领村民向绝壁挑战，历经7年时间在悬崖绝壁上凿出一条“天路”。2005年，毛相林又带领村民脱贫攻坚，历经13年时间探索培育出“三色”经济。2019年9月，入选“中国好人榜”。2021年2月17日，毛相林被评为“感动中国2020年度人物”。2021年2月25日，毛相林被授予“全国脱贫攻坚楷模”荣誉称号。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/3.png" width="100%"
							height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>楷模介绍</h3>
						<text class="u-line-5">云南丽江华坪女子高中校长，最美乡村教师，中国好人榜”敬业奉献好人，全国教书育人楷模……她被授予过40多项荣誉称号。她说：“贫困是女孩儿的隐私”，所以，在她的眼里没有“贫困女生”，只有“大山里的女孩儿”。她坚守滇西贫困地区40多年，建成了全国第一所全免费女子高中。中共中央宣传部12月11日授予张桂梅“时代楷模”称号。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/4.png" width="100%"
							height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>楷模介绍</h3>
						<text class="u-line-5">南仁东，他是国内首屈一指的天文学家，为祖国设计国之重器，让他国望而生畏。他又是“ 中国天眼 ”的主要发起者和奠基人，“ 人民科学家 ”国家荣誉称号的获得者，身患肺癌手术中伤及声带，却依旧为国家事业燃尽生命，他是被誉为“中国天眼之父”的前任FAST工程首席科学家兼总工程师。2017年5月，获得全国创新争先奖； 2017年7月，入选为2017年中国科学院院士增选初步候选人。2017年9月15日晚，南仁东因肺癌逝世，享年72岁。</text>
					</u-col>
				</u-row>
			</view>
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
			tokaimo_De(){
				uni.navigateTo({
					url:'kaimo_de'
				})
			},
		}
	}
</script>

<style scoped>
	.kaimo {
		margin: 10rpx;
		padding: 10rpx;
		border: solid 2rpx #CCC;
		border-radius: 20rpx;
	}
</style>
