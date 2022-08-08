<template>
	<div>
		<div class="container">
			<div class="review">
				孙燕姿导师评语：这位同学唱功基础扎实，转音和高低音的切换非常自然，整首歌曲感情饱满，
				非常不错。整首歌曲感情饱满，非常不错。整首歌曲感情饱满，非常不错。整首歌曲感情饱满，
				非常不错。整首歌曲感情饱满，非常不错。
			</div>
		</div>
	</div>
</template>
<script>
import $ from 'jquery'
$(function () {
	var collapseDefaultContent = '... <i class="icon-plus"></i>点击展开';
	var collapseActiveContent = '<i class="icon-reduce"></i>点击收起';

	Array.from($('.review')).forEach(function (v, i) {
		// 1.5: line-height
		// 14: font-size
		// 2: 超过两行省略
		if (v.clientHeight > (1.5 * 14 * 2)) {
			var el = document.createElement('span');
			el.innerHTML = collapseDefaultContent;
			el.className = 'collapse';
			// 由于每条评论相间背景
			el.style.backgroundColor = i % 2 == 0 ? '#ffca48' : '#ffd358';
			v.appendChild(el);
			// multi 是显示溢出的标志
			$(v).addClass('multi ellipsis')
		}
	})
	// 点击判断收起还是展开
	$('.multi').on('click', '.collapse', function () {
		var $this = $(this)
		var $parent = $this.closest('.multi')

		if ($parent.hasClass('ellipsis')) {
			$parent.removeClass('ellipsis');
			$this.html(collapseActiveContent);
		} else {
			$parent.addClass('ellipsis');
			$this.html(collapseDefaultContent);
		}
	})
})
export default {

	data() {
		return {

		}
	},
	created() {

	},
	methods: {

	},

}
</script>


<style lang="less" rel="stylesheet/less" scoped>
.container {
	width: 375px;
}

.review:nth-child(2n) {
	background: #ffd358;
}

.review:nth-child(2n + 1) {
	background: #ffca48;
}

.review {
	position: relative;
	padding: 0 5px;
	line-height: 1.5em;
	border: 10px solid transparent;
	text-align: justify;
	font-size: 14px;
	color: #b85423;
}

.ellipsis {
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box;
	-webkit-line-clamp: 2;
	-webkit-box-orient: vertical;
}

.collapse {
	padding-right: 5px;
	position: absolute;
	right: 0;
	bottom: 0;
	line-height: 1.5em;
	cursor: pointer;
}

.collapse i {
	width: 15px;
	height: 15px;
	margin-top: -3px;
	display: inline-block;
	vertical-align: middle;
}

.collapse i.icon-reduce {
	background-image: url('../assets/down.png');
	background-size: 100% auto;
}

.collapse i.icon-plus {
	background-image: url('../assets/packup.png');
	background-size: 100% auto;
}
</style>