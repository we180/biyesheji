<template>
	<view>
		<view class="">
			<u-icon name="account" size="32"></u-icon>
			<text>未选中</text>
			<u-icon name="account-fill" size="32"></u-icon>
			<text>已选中</text>
		</view>
		<u-table>
			<block v-for="(item,index) in maxRow" :key="index">
				<u-tr>
					<block v-for="(item1,index1) in cols[index]" :key="index1">
						<u-td>
							<u-icon @click="item1.selected=!item1.selected;" size="32" :name="item1.selected?'account-fill':'account'"></u-icon>
						</u-td>
					</block>
				</u-tr>
			</block>
		</u-table>
		<view class="">
			当前选中:<text>{{selString}}</text>座位
			<u-button type="success" @click="toqrcode()">确定</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				roomId:12,
				roomRows:[],
				maxRow:0,
				cols:[],
				selString:''
			}
		},
		methods: {
			toqrcode(){
				if(this.selString.length<5){
					this.$u.toast('请选择座位')
				}else{
					uni.navigateTo({
						url:'getcode'
					})
				}
			},
		},
		watch:{
			cols:{
				deep:true,
				handler(newVal){
					let list=newVal.flat().filter(res=>res.selected).map(res=>`第${res.row}排第${res.col}个`)
					this.selString=list.join('')
				}
			}
		},
		async onLoad() {
			this.roomRows=(await this.$u.get('/prod-api/api/movie/theatre/seat/list?roomId='+this.roomId)).rows.map(res=>{
				res.selected=false
				return res
			})
			let rowArr=this.roomRows.map(res=>parseInt(res.row))
			let maxRow=Math.max(...rowArr)
			this.maxRow=maxRow+1
			for (let i = 0; i < maxRow; i++) {
				let colArr=this.roomRows.filter(item=>item.row===`${i+1}`)
				this.cols.push(colArr)
			}
		}
	}
</script>

<style scoped>

</style>
