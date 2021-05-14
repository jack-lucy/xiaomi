<template>
  <div class="home-tool-bar">
    <!-- 小工具 -->
    <a v-for="item in info" :href="item.url">
      <div :class="item.class" class="iconfont"></div>
      <span>{{ item.name }}</span>
    </a>
    <!-- 回到顶部 -->
    <a
      href="javascript:void(0);"
      class="backtop"
      v-show="backtopFlag"
      @click="backtop()"
    >
      <div class="iconfont icon-huidingbu back-top"></div>
      <span>回到顶部</span>
    </a>
  </div>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {
      // '回到顶部'工具隐藏和显示标志
      backtopFlag: false,
      // 下拉多少距离，出现'回到顶部'工具
      distance: 1000,
      info: [
        { url: "", name: "个人中心", class: "icon-shouji" },
        {
          url: "https://account.xiaomi.com/",
          name: "个人中心",
          class: "icon-geren",
        },
        {
          url: "https://www.mi.com/service/aftersale/front",
          name: "售后维护",
          class: "icon-editor2",
        },
        {
          url: "https://account.xiaomi.com/",
          name: "人工客服",
          class: "icon-kefu",
        },
        {
          url: "https://www.mi.com/buy/cart",
          name: "购物车",
          class: "icon-gouwuche",
        },
      ],
    };
  },

  methods: {
    // 点击图片回到顶部方法，加计时器是为了过渡顺滑
    backtop() {
      const that = this;
      let timer = setInterval(() => {
        let ispeed = Math.floor(-that.scrollTop / 5);
        document.documentElement.scrollTop = document.body.scrollTop =
          that.scrollTop + ispeed;
        if (that.scrollTop === 0) {
          clearInterval(timer);
        }
      }, 16);
    },

    // 为了计算距离顶部的高度，当高度大于distance显示回顶部图标，小于distance则隐藏
    scrollToTop() {
      const that = this;
      // documentElement 对应的是 html 标签
      let scrollTop =
        window.pageYOffset ||
        document.documentElement.scrollTop ||
        document.body.scrollTop;
      that.scrollTop = scrollTop;
      if (that.scrollTop > that.distance) {
        that.backtopFlag = true;
      } else {
        that.backtopFlag = false;
      }
    },
  },
  // 对scroll进行监听
  mounted() {
    window.addEventListener("scroll", this.scrollToTop);
    // 这里的对象是vue实例
    // console.log(this);
  },
  destroyed() {
    window.removeEventListener("scroll", this.scrollToTop);
  },
};
</script>

<style scoped>
.home-tool-bar {
  position: fixed;
  bottom: 70px;
  right: 0;
  z-index: 99;
}
.home-tool-bar a {
  position: relative;
  display: block;
  width: 82px;
  height: 90px;
  margin-top: -1px;
  background-color: #fff;
  border: 1px solid #f5f5f5;
  text-align: center;
}
.iconfont {
  position: relative;
  margin: 0 auto 8px;
  padding-top: 18px;
  line-height: 30px;
  font-size: 30px;
  color: #757575;
}
.home-tool-bar span {
  color: #757575;
}
.home-tool-bar span:hover {
  color: #ff6700;
}

/* 回到顶部 */
.home-tool-bar .backtop {
  margin-top: 14px;
}
</style>