<template>
	<view style="height: 100%; width: 100%;">
		<mescroll-uni ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback" :down="downOption"
			:up="upOption">
			<view class="">
				<uni-datetime-picker v-model="range" type="daterange" rangeSeparator="至" />
			</view>
			<view class="example-body">
				<!-- 标题卡片模式 -->
				<uni-card title="2021年9月5日" mode="title" :is-shadow="true" note="Tips">
					content
				</uni-card>
				<uni-card title="2021年9月6日" mode="title" :is-shadow="true" note="Tips">
					content
				</uni-card>
				<uni-card title="xxxx年x月x日" mode="title" :is-shadow="true" note="Tips">
					content
				</uni-card>
				<uni-card title="xxxx年xx月x日" mode="title" :is-shadow="true" note="Tips">
					content
				</uni-card>
				<view>

				</view>
			</view>
		</mescroll-uni>
		<uni-fab :pattern="fabSetting.pattern" :horizontal="fabSetting.horizontal" :vertical="fabSetting.vertical"
			:direction="fabSetting.direction" @fabClick="fabClick" :popMenu="false"></uni-fab>
	</view>
</template>

<script>
	export default {
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
			}
		},
		methods: {
			fabClick() {
				uni.navigateTo({
					url: "form/addForm"
				})
			},
			upCallback(page) {
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

<style>
</style>
