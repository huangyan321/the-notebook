<template>
	<view style="width: 100%;height: 100%;">
		<mescroll-uni ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback" :down="downOption"
			:up="upOption">
			<view class="example-body">
				<uni-datetime-picker v-model="range" type="daterange" rangeSeparator="至" />
			</view>
			<view class="picker">
				<view class="picker-item">
					<view class="left-text">
						选择类型
					</view>
					<view class="db">
						<picker @change="bindPickerChange" :value="index" :range="array">
							<view class="select-input">{{array[index]}}</view>
						</picker>
					</view>
				</view>
			</view>

			<!-- 标题卡片模式 -->
			<uni-card mode="basic" :is-shadow="true" :note="item.state === '1' ? array[0] : array[1]"
				v-for="(item,index) in recordList" :keys="index">
				<view class="detail">
					<uni-table border stripe emptyText="暂无更多数据">
						<!-- 表头行 -->
						<uni-tr>
							<uni-th align="center" width="100">金额</uni-th>
							<uni-th align="center">备注</uni-th>
						</uni-tr>
						<!-- 表格数据行 -->
						<uni-tr>
							<uni-td align="center">{{item.amount}}元</uni-td>
							<uni-td>{{item.remark}}</uni-td>
						</uni-tr>
					</uni-table>
				</view>
			</uni-card>
		</mescroll-uni>
		<view>
			<uni-fab :pattern="fabSetting.pattern" :horizontal="fabSetting.horizontal" :vertical="fabSetting.vertical"
				:direction="fabSetting.direction" @fabClick="fabClick" :popMenu="false"></uni-fab>
		</view>
	</view>
</template>

<script>
	export default {
		name: "cashbook",
		data() {
			return {
				fabSetting: {
					range: ['2021-03-8', '2021-4-20'],
					pattern: {
						buttonColor: "pink"
					},
					horizontal: "right",
					vertical: "bottom",
					direction: "vertical",
				},
				downOption: {},
				upOption: {
					page: {
						size: 10, // 每页数据的数量,默认10，
					},
					noMoreSize: 5, // 配置列表的总数量要大于等于5条才显示'-- END --'的提示
					empty: {
						tip: '暂无相关数据'
					}
				},
				array: ["收入", "支出"],
				index: 0,
				recordList: [{
						state: "0",
						amount: 100,
						remark: "早上吃了包子"
					},
					{
						state: "1",
						amount: 200,
						remark: "捡破烂"
					},
					{
						state: "0",
						amount: 50,
						remark: "吃零食"
					},
					{
						state: "0",
						amount: 500,
						remark: "玩"
					},
					{
						state: "0",
						amount: 100,
						remark: "快乐地瓜yyds好喝到跺jiojio看到个死肥宅一直盯着人家看的我都害怕了今天也是在逃公主的一天吖"
					}
				]
			}
		},
		methods: {
			bindPickerChange(EventHandle) {
				this.index = EventHandle.detail.value
			},
			fabClick() {
				uni.navigateTo({
					url: "form/addForm"
				})
			},
			async upCallback(page) {
				let pagenum = page.num; // 页码, 默认从1开始
				let pagesize = page.size; // 页长, 默认每页10条
				// const res = await getOrderList({
				// 	pagenum,
				// 	pagesize
				// });
				// res.meta.status === 200 ?
				// 	(() => {
				// 		// 接口返回的当前页数据列表 (数组)
				// 		let curPageData = res.data.goods;
				// 		// 接口返回的当前页数据长度 (如列表有26个数据,当前页返回8个,则curPageLen=8)
				// 		let curPageLen = res.data.goods.length;
				// 		// 接口返回的总数据量(如列表有26个数据,每页10条,共3页; 则totalSize=26)
				// 		let totalSize = res.data.total;
				// 		// 接口返回的是否有下一页 (true/false)
				// 		// let hasNext = data.xxx;
				// 		//设置列表数据
				// 		if (page.num == 1) {
				// 			this.orderList = []
				// 		}; //如果是第一页需手动置空列表
				// 		this.orderList = this.orderList.concat(curPageData); //追加新数据
				// 		this.mescroll.endBySize(curPageLen, totalSize);
				// 	})() : this.mescroll.endErr()

			},
		}
	}
</script>

<style scoped>
	.picker {
		width: 50%;
		background-color: #fff;
		position: relative;
		margin-top: 20rpx;
		display: flex;
		flex-direction: column;
	}

	.picker::before {
		position: absolute;
		z-index: 10;
		right: 0;
		top: 0;
		left: 0;
		height: 1px;
		content: "";
		background-color: #c8c7cc;
	}

	.picker-item {
		position: relative;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}

	.picker-item::after {
		position: absolute;
		z-index: 3;
		right: 0;
		bottom: 0;
		left: 15px;
		height: 1px;
		content: "";
		background-color: #c8c7cc;
	}

	.picker::after {
		position: absolute;
		z-index: 10;
		right: 0;
		bottom: 0;
		left: 0;
		height: 1px;
		content: "";
		background-color: #c8c7cc;
	}

	.left-text {
		white-space: nowrap;
		font-size: 14px;
		padding: 0 15px;

	}

	.db {
		flex: 1;
	}

	.select-input {
		height: 25px;
		padding: 7px 12px;
		line-height: 25px;
		font-size: 14px;
		background: #fff;
		flex: 1;
	}

	.time-picker {
		width: 100%;
		height: 100%;
	}

	.detail {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}

	.left-marks {
		width: auto;
	}

	.right-pay-count {
		width: 30%;
	}
</style>
