<template>
  <div class="text">
    <span :style="{ 'max-height': textOpenFlag ? textHeight : '' }" :class="{ unfoldText: textOpenFlag }"
      class="titleText" ref="desc">
      {{ text }}
    </span>
    <span v-if="showBtnFlag" @click="textOpenFlag = !textOpenFlag" class="btn">
      {{ textOpenFlag ? "展开" : "收起" }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: '记忆对文字巴楞记忆对文字记忆对文字巴楞记忆对文字文字巴楞记忆对文字巴楞记忆对文字巴楞记楞遇到一个应该都已经dihughyfg打开的环境',
      textHeight: false,
      textOpenFlag: false,
      showBtnFlag: false
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.calculateText()
    })
  },
  methods: {
    calculateText() {
      let twoHeight = 28 * 3;
      this.textHeight = `${twoHeight}px`
      let curHeight = this.$refs.desc.offsetHeight;
      if (curHeight > twoHeight) {
        this.textOpenFlag = true;
        this.showBtnFlag = true;
      } else {
        this.textOpenFlag = false;
        this.showBtnFlag = false
      }
    }
  },
};
</script>
<style scoped>
.text {
  /* width: 100px; */
  position: relative;
  margin-bottom: 20px;
}

.titleText {
  font-size: 18px;
  line-height: 28px;
}

.unfoldText {
  overflow: hidden;
  display: block;
}

.unfoldText:after {
  z-index: 53;
  content: "...";
  position: absolute;
  bottom: 0;
  right: 80px;
  width: 20px;
  padding-left: 30px;
  background: linear-gradient(to right, rgba(255, 255, 255, 0.1), #fff 45%);
}

.btn {
  height: 25px;
  font-size: 14px;
  color: #5864ff;
  position: absolute;
  right: 0;
  bottom: 2px;
  margin-left: 60px;
  background: #fff;
  width: 80px;
  text-align: center;
  line-height: 30px;
}
</style>

