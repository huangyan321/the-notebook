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
			<uni-card  mode="basic" :is-shadow="true" note="支出" extra="12元">
				<view class="detail">
					<view class="left-marks">
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
					</view>
					<view class="right-pay-count">
						12元
					</view>
				</view>
			</uni-card>
			<uni-card  mode="basic" :is-shadow="true" note="支出" extra="12元">
				<view class="detail">
					<view class="left-marks">
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
					</view>
					<view class="right-pay-count">
						12元
					</view>
				</view>
			</uni-card>
			<uni-card  mode="basic" :is-shadow="true" note="支出" extra="12元">
				<view class="detail">
					<view class="left-marks">
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
					</view>
					<view class="right-pay-count">
						12元
					</view>
				</view>
			</uni-card>
			<uni-card  mode="basic" :is-shadow="true" note="支出" extra="12元">
				<view class="detail">
					<view class="left-marks">
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
					</view>
					<view class="right-pay-count">
						12元
					</view>
				</view>
			</uni-card>
			<uni-card  mode="basic" :is-shadow="true" note="支出" extra="12元">
				<view class="detail">
					<view class="left-marks">
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
						这里是内容区域
					</view>
					<view class="right-pay-count">
						12元
					</view>
				</view>
			</uni-card>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: "cashbook",
		data() {
			return {
				array: ["收入", "支出"],
				index: 0,
			}
		},
		methods: {
			bindPickerChange(EventHandle) {
				this.index = EventHandle.detail.value
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
