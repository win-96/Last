<template>
	<div class="content-wrap">
		<div
			:class="['content', expande ? 'expande' : 'close']"
			ref="content"
		>
			{{list.test}}
		</div>
		<div
			class="expande-button-wrap"
			v-if="needShowExpande"
		>
			<div
				class="expande-button"
				@click="expandeClick"
				v-if="!expande"
			>
				<span style="color: black">...</span><img
					src="../assets/down.png"
					alt=""
				>
			</div>
			<div
				class="expande-button"
				@click="expandeClick"
				v-else
			><img
					src="../assets/packup.png"
					alt=""
				></div>
		</div>
	</div>
</template>


<script>
export default {
	name: 'HelloWorld',
	data() {
		return {
			expande: true,
			needShowExpande: false,
			list: {
				test: '思路：1、判断当前内容是否超过三行。此处可以给每行设置一个行高line-height,渲染完后超过三倍的行高即认为是内容超过了三行。2、展示/收起状态的切换可以通过data中的参数来绑定。3、在底部使用position:absolute来绝对定位展开该在的位置。4、根据业务需求来设定好展开和收起按钮需要呆的地方。'
			}
		}
	},
	methods: {
		expandeClick() {
			console.log('expandeClick')
			this.$refs.content.innerHTML = this.list.test
			if (this.expande) {
				console.log(1);
				let result = this.$refs.content.innerHTML.slice(0, 89)
				this.$refs.content.innerHTML = result
			} else {
				console.log(2);
				this.$refs.content.innerHTML = this.list.test
			}
			this.expande = !this.expande
		},
	},
	mounted() {
		this.$nextTick(() => {
			let lineHeight = 22
			if (this.$refs.content.offsetHeight > lineHeight * 3) {
				this.expande = false
				this.needShowExpande = true
				// console.log(this.$refs.content.offsetHeight);
				let result = this.$refs.content.innerHTML.slice(0, 90)
				this.$refs.content.innerHTML = result
			} else {
				this.expande = true
				console.log(111);
			}
		})
	},
}
</script>


<style lang="less" rel="stylesheet/less" scoped>
.expande {
	height: auto;
}
.content {
	text-align: left;
}
.expande-button-wrap {
	position: relative;
}
.close {
	height: 65px;
	overflow: hidden;
}
.expande-button {
	position: absolute;
	bottom: 0;
	right: 3px;
}
</style>