<template>
	<view>
		<view class="story_list">
			<view class="story" @click="tohero_story_De">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/W020211011361082051645.png" width="100%" height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>英雄事迹介绍</h3>
						<text class="u-line-5">[28] 9月17日13时30分许，神舟十二号载人飞船返回舱安全降落在东风着陆场预定区域。 [30-31] 2021年11月23日，中共中央、国务院、中央军委给聂海胜颁发“一级航天功勋奖章”</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/5.png" width="100%" height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>英雄事迹介绍</h3>
						<text class="u-line-5">王银虎，中国人民解放军战斗英雄。1926年出生于河北省赞皇县。1944年8月，参加八路军，1946年4月,加入中国共产党。3次受奖，4次立功。1947年进军大别山时任排长,在艰苦困难的环境中，他注重做思想政治工作，并以自己的模范行动帮助战士克服困难，鼓舞斗志，被评为“模范共产党员”。1949年12月，王银虎任副政治指导员时，在四川省大邑县战斗中，带领部队发挥夜战优势，智俘守河国民党军一个连。随后，又率领11名战士攻进城南关，突入国民党军团部，在众寡悬殊的情况下,他配合军事打击,开展政治攻势,迫使其团长带领所属15个连队缴械投降,缴获29辆满载军用物资的卡车。1950年 9月，被中国人民解放军西南军区评为“特等杀敌英雄”，并出席了中华人民共和国全国战斗英雄代表会议。后任指导员、教导员、团政治委员、师副政治委员、省军区后勤部政治委员等职。1983年12月，离职休养，离休前任中国人民解放军福建省军区后勤部政治委员。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/6.png" width="100%" height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>英雄事迹介绍</h3>
						<text class="u-line-5">万山丛中抗日英雄真不少，青纱帐里游击健儿逞英豪。”抗战时期，每当太阳升起时，文昌一所小学校的操场上就会传来抗日儿童团铿锵有力的《黄河大合唱》。年仅十几岁的郑浩是该活动的组织者。如今，91岁高龄的郑浩永远忘不掉当时孩子们眉头紧锁、眼神坚毅、拳头紧握的神情。身为文昌市宝芳乡南兴村抗日儿童团团长、后备队队长的郑浩和他们一样，热血沸腾，心中满是对日本人的愤恨，以及“不愿做亡国奴”的革命热情。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/7.png" width="100%" height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>英雄事迹介绍</h3>
						<text class="u-line-5">16岁那年，杨占山成为东北民主联军的一员，此后，跟随部队转战南北。1949年12月，部队开到雷州半岛，准备渡海作战，杨占山已是43军129师385团二营机炮连一班班长。杨占山记得，第一次看到大海时，心情虽然很高兴，但眼前的大海给他的感觉又很奇怪，仿佛望着一只怪物。 “年纪不大的战士还有些害怕，当时就想，这么大一片海怎么过？”很快，解放军战士克服了心理上的恐惧，加紧练兵。当时解放军战士甚至喊出了口号： “一定要把陆军练成‘海军’，誓变猛虎为蛟龙，练成既能陆战又能海战的英雄连队”。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_kaimo/8.png" width="100%" height="250rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>英雄事迹介绍</h3>
						<text class="u-line-5">阳鹏，男，汉族，1984年10月生，中共党员，中国人民解放军91991部队后勤部助理员。面对犯罪分子在大巴车上突然纵火，阳鹏挺身而出，把生的希望给了旅客，把死的危险留给了自己，忠实践行了人民子弟兵全心全意为人民服务的宗旨和当代革命军人核心价值观。</text>
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
			tohero_story_De(){
				uni.navigateTo({
					url:'hero_story_de'
				})
			},
		}
	}
</script>

<style scoped>
	.story{
		margin: 10rpx;
		padding: 10rpx;
		border: solid 2rpx #CCC;
		border-radius: 20rpx;
	}
</style>
