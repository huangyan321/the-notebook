<template>
	<view style="height: 100%; width: 100%;">
		<view class="example-body">
			<uni-datetime-picker v-model="range" type="daterange" rangeSeparator="至" />
		</view>
		<scroll-view>
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
		</scroll-view>
		<view>
			<uni-fab :pattern="fabSetting.pattern" :horizontal="fabSetting.horizontal" :vertical="fabSetting.vertical" :direction="fabSetting.direction"
				@fabClick="fabClick" :popMenu="false"></uni-fab>
		</view>
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
				}

			}
		},
		methods: {
			fabClick() {
				uni.navigateTo({
					url: "form/addForm"
				})
			}
		}
	}
</script>

<style>
</style>
