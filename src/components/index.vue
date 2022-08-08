<template>
	<div>
		<div class="content">
			<div :class="n % 2 == 0 ? 'text' : 'fl'">
				<label
					:class="n % 2 != 0 ? 'btn fixed' : 'btn'"
					for="exp"
					v-if="flag"
				>
					<!-- {{ n % 2 != 0 ? '↑' : '↓' }} -->
					<div
						v-if="n%2!=0"
						@click="btn"
					><svg
							class="icon"
							width="16px"
							height="16.00px"
							viewBox="0 0 1024 1024"
							version="1.1"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								fill="#333333"
								d="M830.24 685.76l11.328-11.312a16 16 0 0 0 0-22.64L530.448 340.688a16 16 0 0 0-22.64 0L196.688 651.808a16 16 0 0 0 0 22.64l11.312 11.312a16 16 0 0 0 22.624 0l288.496-288.512L807.632 685.76a16 16 0 0 0 22.624 0z"
							/>
						</svg></div>
					<div
						v-else
						@click="btn"
					><svg
							class="icon"
							width="16px"
							height="16.00px"
							viewBox="0 0 1024 1024"
							version="1.1"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								fill="#333333"
								d="M830.24 340.688l11.328 11.312a16 16 0 0 1 0 22.624L530.448 685.76a16 16 0 0 1-22.64 0L196.688 374.624a16 16 0 0 1 0-22.624l11.312-11.312a16 16 0 0 1 22.624 0l288.496 288.496 288.512-288.496a16 16 0 0 1 22.624 0z"
							/>
						</svg></div>
				</label>
				<span
					class="fl"
					ref="p"
				>
					但听得蹄声如雷，到近处，拉马向两旁一分，最后一骑从中驰出但听得蹄声如雷，到近处，拉马向两旁一分，最从中驰出但听得蹄声如雷，到近处，拉马向两旁一分，最后一骑从中驰出但听得蹄声如雷，到近处，拉马向两旁一分，最后一骑从中驰出</span>
				<!-- <div class="rbBlock">&emsp;&emsp;&emsp;</div> -->
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			n: 0,
			flag: false
		}
	},
	created() {

	},
	methods: {
		btn() {
			this.n++
		},
		init() {
			console.log(this.$refs.p.innerHTML.length);
			if (this.$refs.p.innerHTML.length < 36) {
				this.flag = false
			} else {
				this.flag = true
			}
		}
	},
	mounted() {
		this.init()
	}
}
</script>

<style scoped>
.content {
	display: flex;
	width: 197px;
	font-size: 16px;
}

.text::before {
	content: '';
	float: right;
	height: 100%;
	margin-bottom: -20px;
}

.content > div {
	position: relative;
}

.btn {
	float: right;
	clear: both;
	margin-right: 4px;
	background: #fff;
}

.fixed {
	position: absolute;
	right: 0;
	bottom: 0;
}

.rbBlock {
	width: 32px;
	height: 20px;
	display: inline-block;
}

.text {
	display: -webkit-box;
	overflow: hidden;
	-webkit-line-clamp: 3;
	-webkit-box-orient: vertical;
	text-align: left;
}
.fl {
	text-align: left;
}
</style>