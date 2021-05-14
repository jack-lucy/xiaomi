<template>
  <!-- 最顶部topbar区域 -->
  <header class="site-topbar">
    <div class="content">
      <!-- 左侧导航栏 -->
      <div class="topbar-nav">
        <ul class="topbar-nav-ul">
          <!-- 这里设计和小米官网有所不同 -->
          <li v-for="(item, index) in navs" class="nofollow">
            <!-- "小米商城"这个链接和其他链接跳转方式有所不同-->
            <template v-if="item.name === '小米商城'">
              <a :href="item.sourceUrl">{{ item.name }}</a>
            </template>
            <template v-else>
              <a
                :href="item.sourceUrl"
                target="_blank"
                @mouseenter="showCode(index)"
                @mouseleave="hideCode(index)"
                >{{ item.name }}</a
              >
              <!-- 二维码显示 -->
              <transition name="miCode">
                <!-- 我们可以给showCode设置一个参数，如果参数符合则显示二维码 -->
                <span
                  v-show="codeStatus"
                  class="appcode"
                  @mouseenter="showCode(100)"
                  ref="appcode"
                  @mouseleave="hideCode()"
                >
                  <!-- 三角形 -->
                  <span></span>
                  <img
                    src="//i1.mifile.cn/f/i/17/appdownload/download.png?"
                    alt=""
                  />
                  <div>小米商品app</div>
                </span>
              </transition>
            </template>
            <span v-if="index !== 12" class="sep">|</span>
          </li>
        </ul>
      </div>

      <!-- 购物车 -->
      <div
        class="topbar-cart"
        :class="{ changeBg: cartStatus }"
        @mouseenter="showCart"
        @mouseleave="hideCart"
      >
        <i class="iconfont icon-gouwuche"></i>
        <a
          href="https://www.mi.com/buy/cart"
          :class="{ changeText: cartStatus }"
          >购物车(0)</a
        >
        <transition>
          <div v-show="cartStatus" class="msg">
            购物车中还没有商品，赶紧选购吧！
          </div>
        </transition>
      </div>

      <!-- 登录、注册 -->
      <div class="topbar-info">
        <a
          href="https://account.xiaomi.com/fe/service/login/password"
          class="link"
          >登录</a
        ><span>|</span>
        <a href="https://cn.account.xiaomi.com/pass/register?" class="link"
          >注册</a
        ><span>|</span>
        <a href="#">消息通知</a>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {
      navs: [
        { name: "小米商城", sourceUrl: "http://www.mi.com/index.html" },
        { name: "MIUI", sourceUrl: "http://www.miui.com/" },
        { name: "IoT", sourceUrl: "https://iot.mi.com/" },
        { name: "云服务", sourceUrl: "https://i.mi.com/" },
        { name: "天星数科", sourceUrl: "https://airstar.com/home" },
        { name: "有品", sourceUrl: "https://www.xiaomiyoupin.com/" },
        { name: "小爱开放平台", sourceUrl: "https://xiaoai.mi.com/" },
        { name: "企业团购", sourceUrl: "https://qiye.mi.com/" },
        {
          name: "资质证照",
          sourceUrl: "https://www.mi.com/aptitude/list?id=41",
        },
        { name: "协议规则", sourceUrl: "https://www.mi.com/aptitude/list" },
        { name: "下载app", sourceUrl: "https://www.mi.com/appdownload" },
        {
          name: "智能生活",
          sourceUrl: "https://xiaomishare.mi.com/?from=micom#/",
        },
        { name: "Select Location", sourceUrl: "http://www.mi.com/index.html" },
      ],
      codeStatus: false,
      cartStatus: false,
    };
  },
  methods: {
    // 如果index是10，或者是我们指定的100即可显示二维码
    showCode(index) {
      if (index === 10 || index === 100) {
        this.codeStatus = true;
      }
      // console.log(this.codeStatus);
    },
    hideCode() {
      this.codeStatus = false;
      // console.log(this.codeStatus);
    },
    showCart() {
      this.cartStatus = true;
      clearInterval(this.timer2);
    },
    hideCart() {
      let self = this;
      this.timer2 = setTimeout(function () {
        self.cartStatus = false;
      }, 300);
      // console.log(self === this);
    },
  },
};
</script>

<style scoped>
.site-topbar {
  position: relative;
  width: 100%;
  z-index: 30;
  height: 40px;
  font-size: 12px;
  color: #b0b0b0;
  background: #333;
}
.content {
  margin: 0 auto;
  width: 1226px;
}
/* 1.左侧导航栏 */
.topbar-nav {
  display: inline-block;
  width: 794.13px;
  height: 40px;
}
.nofollow {
  display: inline-block;
}
.site-topbar a {
  display: inline-block;
  color: #b0b0b0;
  line-height: 40px;
}
.site-topbar a:hover {
  color: #fff;
}
/* 二维码区域 */
.appcode {
  position: absolute;
  top: 40px;
  width: 124px;
  height: 148px;
  background: #fff;
  left: 690px;
  text-align: center;
  font-size: 14px;
  -webkit-box-shadow: #aaa 0 1px 5px;
  box-shadow: 0 1px 5px #aaa;
}
/* 动画显示，这里有个小bug：二维码图片会立即显示，不会像小米官网那样，有个过渡和柔和的过程 */
.miCode-enter-active,
.miCode-leave-active {
  transition: all 0.3s ease;
  height: 100px;
}
.miCode-enter,
.miCode-leave-to {
  height: 0;
}
.appcode img {
  margin-top: 20px;
  width: 90px;
  height: 90px;
}
/* 三角设计 宽和高必须为0，注意top值设计*/
.appcode span {
  position: absolute;
  left: 50px;
  top: -20px;
  width: 0;
  height: 0;
  line-height: 0;
  font-size: 0;
  border: 10px solid transparent;
  border-bottom-color: #fff;
}
.nofollow .sep {
  margin: 0 5px;
  color: #424242;
}
/* 2.右侧购物车区域  右浮*/
.topbar-cart {
  position: relative;
  float: right;
  width: 120px;
  height: 40px;
  line-height: 40px;
  margin-left: 15px;
  font-size: 12px;
  text-align: center;
  background: #424242;
}
/*这个设计很low，不好
   a.改变背景和iconfont */
.changeBg {
  background: #fff;
  color: #ff6700;
}
/* b.改变a标签里面的字体"购物车" */
.topbar-cart .changeText {
  color: #ff6700;
}
/* c.这里是把前面的hover覆盖掉，设计得很不好 */
.site-topbar .changeText:hover {
  color: #ff6700;
}
.msg {
  position: absolute;
  right: 0;
  top: 40px;
  z-index: 31;
  width: 316px;
  height: 100px;
  color: #424242;
  background: #fff;
  line-height: 100px;
  -webkit-box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
}
.v-enter-active,
.v-leave-active {
  transition: all 0.3s ease;
  height: 100px;
}
.v-enter,
.v-leave-to {
  height: 0;
}

/* 3.登录信息 */
.topbar-info {
  position: relative;
  float: right;
  height: 40px;
  line-height: 40px;
}
.topbar-info .link {
  padding: 0 5px;
  text-align: center;
}
.topbar-info span {
  color: #424242;
}
</style>