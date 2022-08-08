<template>
  <div>
    <div class="content">
      <div :class="n % 2 == 0 ? 'text' : 'fl'">
        <label :class="n % 2 != 0 ? 'btn fixed' : 'btn'" for="exp" v-if="flag">
          <div v-if="n % 2 != 0" @click="btn">
            <van-icon name="arrow-up" />收起
          </div>
          <div v-else @click="btn">
            <van-icon name="arrow-down" /> 展开
          </div>
        </label>
        <span class="fl" ref="p">
          但听得蹄声如雷，到近处，
          拉马向两旁一分，
          最后一骑从中驰出
          但听得蹄声如雷，
          到近处，
          <!-- 拉马向两旁一分，最从中驰出但听得蹄声如雷，到近处，拉马向两旁一分，
          最后一骑从中驰出但听得蹄声如雷，到近处，拉马向两旁一分，最后一骑从中驰出 -->
        </span>
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
      // console.log(this.$refs.p.innerHTML.length);
      if (this.$refs.p.innerHTML.length < 39) {
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

.content>div {
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