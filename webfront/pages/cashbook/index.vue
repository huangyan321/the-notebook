<template>
	<view style="width: 100%;height: 100%;">
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
		<scroll-view>
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
		</scroll-view>
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
			}
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
