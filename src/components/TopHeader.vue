<template>
  <div class="site-header">
    <div class="contain">
      <!-- logo区域 -->
      <div class="header-logo top-item">
        <a href="https://www.mi.com/index.html">
          <img
            src="http://s02.mifile.cn/assets/static/image/logo-mi2.png"
            alt=""
          />
        </a>
      </div>
      <!-- 导航栏 -->
      <div class="header-nav top-item">
        <ul>
          <li id="J_navCategory">
            <banner-list></banner-list>
          </li>
          <li v-for="(item, index) in navs" class="nav-item">
            <template v-if="item.type">
              <a
                href="javascript: void(0);"
                @mouseenter="showProduct(item.type)"
                @mouseleave="hideProduct()"
              >
                <span>{{ item.name }}</span>
              </a>
            </template>
            <template v-else>
              <a :href="item.sourceUrl">
                <span>{{ item.name }}</span>
              </a>
            </template>
          </li>
        </ul>
      </div>
      <!-- 搜索框 -->
      <div class="header-search">
        <form
          action="//search.mi.com/search"
          method="get"
          class="search-form clearfix"
        >
          <input
            type="text"
            id="text"
            value="红米K30"
            class="search-input"
            @focus="evtIntFocus()"
            @blur="evtIntBlur()"
          />
          <input type="submit" value="搜索" class="search-button" />
        </form>
        <div v-if="hotkeyStatus" class="hotkey" @focus="evtIntFocus()">
          <ul>
            <li v-for="item in hotkey">
              <a :href="item.url">{{ item.name }}</a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <!-- 商品展示 -->
    <transition>
      <div
        v-show="productStatus"
        class="show-product"
        @mouseenter="showProduct()"
        @mouseleave="hideProduct()"
      >
        <div class="contain">
          <ul>
            <li v-for="(item, index) in currentType" class="product-item">
              <i v-if="index !== 0" class="iconfont"></i>
              <a :href="item.src">
                <div class="product-img"><img :src="item.imgUrl" alt="" /></div>
                <div>{{ item.name }}</div>
                <div class="product-text">{{ item.price }}</div>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import BannerList from "./BannerList";
export default {
  components: {
    BannerList,
  },
  name: "",
  data() {
    return {
      productStatus: false,
      hotkeyStatus: false,
      currentType: this.xiaomi,
      navs: [
        { name: "小米手机", type: "xiaomi" },
        { name: "Redmi红米", type: "redmi" },
        { name: "电视", type: "tv" },
        { name: "笔记本", type: "lt" },
        { name: "家电", type: "appliance" },
        { name: "路由器", type: "router" },
        { name: "智能硬件", type: "hardware" },
        { name: "服务", sourceUrl: "//www.mi.com/service/" },
        { name: "社区", sourceUrl: "https://www.xiaomi.cn/" },
      ],
      // 搜索词
      hotkey: [
        {
          url:
            "https://www.mi.com/search?keyword=%E5%85%A8%E9%83%A8%E5%95%86%E5%93%81",
          name: "全部商品",
        },
        {
          url: "https://www.mi.com/search?keyword=%E5%B0%8F%E7%B1%B311  ",
          name: "小米11",
        },
        {
          url:
            "https://www.mi.com/search?keyword=%E5%B0%8F%E7%B1%B3%E6%89%8B%E6%9C%BA",
          name: "小米手机",
        },
        {
          url: "https://www.mi.com/search?keyword=%E6%B4%97%E8%A1%A3%E6%9C%BA",
          name: "洗衣机",
        },
        {
          url: "https://www.mi.com/search?keyword=%E7%A9%BA%E8%B0%83",
          name: "空调",
        },
        {
          url: "https://www.mi.com/search?keyword=%E5%87%80%E6%B0%B4%E5%99%A8",
          name: "净水器",
        },
        {
          url: "https://www.mi.com/search?keyword=%E7%BA%A2%E7%B1%B3",
          name: "红米",
        },
      ],
      xiaomi: [
        {
          name: "小米MIX FOLD",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/85e44ea2405ff8414148bbde7446b137.png",
          url: "https://www.mi.com/mixfold",
          price: "9999元起",
        },
        {
          name: "小米11 Ultra",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/1a359e9346e3c6ee8c9d8389e3fd9458.png",
          url: "https://www.mi.com/mi11ultra",
          price: "5999元起",
        },
        {
          name: "小米11 Pro",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?",
          url: "https://www.mi.com/mi11Pro",
          price: "4999元起",
        },
        {
          name: "小米11 青春版",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/56e3379b5422cb06e5c8a0c546445606.png",
          url: "https://www.mi.com/mi11youth",
          price: "2299元起",
        },
        {
          name: "小米10s",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f9149ef3ba2c9025a4a21c98ae793808.png",
          url: "https://www.mi.com/mi10s",
          price: "3299元起",
        },
        {
          name: "小米11",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/963679eaf3937351e154600ab3448460.png",
          url: "https://www.mi.com/mi11",
          price: "3999元起",
        },
      ],
      redmi: [
        {
          name: "K40 Peo系列",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png",
          url: "https://www.mi.com/redmik40ultra-k40pro",
          price: "2799元起",
        },
        {
          name: "K40 Peo系列",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png",
          url: "https://www.mi.com/redmik40ultra-k40pro",
          price: "2799元起",
        },
        {
          name: "K40 Peo系列",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png",
          url: "https://www.mi.com/redmik40ultra-k40pro",
          price: "2799元起",
        },
        {
          name: "K40 Peo系列",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png",
          url: "https://www.mi.com/redmik40ultra-k40pro",
          price: "2799元起",
        },
        {
          name: "K40 Peo系列",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png",
          url: "https://www.mi.com/redmik40ultra-k40pro",
          price: "2799元起",
        },
        {
          name: "K40 Peo系列",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png",
          url: "https://www.mi.com/redmik40ultra-k40pro",
          price: "2799元起",
        },
      ],
      tv: [
        {
          name: "Redmi MAX 86” 超大屏电视",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8c87fdc4bcfd081ac240f7af1417ce60.png",
          url: "https://www.mi.com/buy/detail?product_id=13498",
          price: "9999元起",
        },
        {
          name: "Redmi MAX 86” 超大屏电视",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8c87fdc4bcfd081ac240f7af1417ce60.png",
          url: "https://www.mi.com/buy/detail?product_id=13498",
          price: "9999元起",
        },
        {
          name: "Redmi MAX 86” 超大屏电视",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8c87fdc4bcfd081ac240f7af1417ce60.png",
          url: "https://www.mi.com/buy/detail?product_id=13498",
          price: "9999元起",
        },
        {
          name: "Redmi MAX 86” 超大屏电视",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8c87fdc4bcfd081ac240f7af1417ce60.png",
          url: "https://www.mi.com/buy/detail?product_id=13498",
          price: "9999元起",
        },
        {
          name: "Redmi MAX 86” 超大屏电视",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8c87fdc4bcfd081ac240f7af1417ce60.png",
          url: "https://www.mi.com/buy/detail?product_id=13498",
          price: "9999元起",
        },
        {
          name: "Redmi MAX 86” 超大屏电视",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8c87fdc4bcfd081ac240f7af1417ce60.png",
          url: "https://www.mi.com/buy/detail?product_id=13498",
          price: "9999元起",
        },
      ],
      lt: [
        {
          name: "小米笔记本Pro 15",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/705cde5b7afce7ee89d95d1a35938778.png",
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          price: "6499元起",
        },
        {
          name: "小米笔记本Pro 15",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/705cde5b7afce7ee89d95d1a35938778.png",
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          price: "6499元起",
        },
        {
          name: "小米笔记本Pro 15",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/705cde5b7afce7ee89d95d1a35938778.png",
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          price: "6499元起",
        },
        {
          name: "小米笔记本Pro 15",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/705cde5b7afce7ee89d95d1a35938778.png",
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          price: "6499元起",
        },
        {
          name: "小米笔记本Pro 15",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/705cde5b7afce7ee89d95d1a35938778.png",
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          price: "6499元起",
        },
        {
          name: "小米笔记本Pro 15",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/705cde5b7afce7ee89d95d1a35938778.png",
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          price: "6499元起",
        },
      ],
      appliance: [
        {
          name: "米家风冷对开门冰箱 483L",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/b7a4e3ff7919ca2407ad970b78abd09a.jpg",
          url: "https://www.mi.com/buy/detail?product_id=10952",
          price: "2499元",
        },
        {
          name: "米家风冷对开门冰箱 483L",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/b7a4e3ff7919ca2407ad970b78abd09a.jpg",
          url: "https://www.mi.com/buy/detail?product_id=10952",
          price: "2499元",
        },
        {
          name: "米家风冷对开门冰箱 483L",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/b7a4e3ff7919ca2407ad970b78abd09a.jpg",
          url: "https://www.mi.com/buy/detail?product_id=10952",
          price: "2499元",
        },
        {
          name: "米家风冷对开门冰箱 483L",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/b7a4e3ff7919ca2407ad970b78abd09a.jpg",
          url: "https://www.mi.com/buy/detail?product_id=10952",
          price: "2499元",
        },
        {
          name: "米家风冷对开门冰箱 483L",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/b7a4e3ff7919ca2407ad970b78abd09a.jpg",
          url: "https://www.mi.com/buy/detail?product_id=10952",
          price: "2499元",
        },
        {
          name: "米家风冷对开门冰箱 483L",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/b7a4e3ff7919ca2407ad970b78abd09a.jpg",
          url: "https://www.mi.com/buy/detail?product_id=10952",
          price: "2499元",
        },
      ],
      router: [
        {
          name: "小米路由器AX6000",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2a759fa795d749f0538cfd2a15890027.png",
          url: "https://www.mi.com/r6000",
          price: "599元",
        },
        {
          name: "小米路由器AX6000",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2a759fa795d749f0538cfd2a15890027.png",
          url: "https://www.mi.com/r6000",
          price: "599元",
        },
        {
          name: "小米路由器AX6000",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2a759fa795d749f0538cfd2a15890027.png",
          url: "https://www.mi.com/r6000",
          price: "599元",
        },
        {
          name: "小米路由器AX6000",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2a759fa795d749f0538cfd2a15890027.png",
          url: "https://www.mi.com/r6000",
          price: "599元",
        },
        {
          name: "小米路由器AX6000",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2a759fa795d749f0538cfd2a15890027.png",
          url: "https://www.mi.com/r6000",
          price: "599元",
        },
        {
          name: "小米路由器AX6000",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2a759fa795d749f0538cfd2a15890027.png",
          url: "https://www.mi.com/r6000",
          price: "599元",
        },
      ],
      hardware: [
        {
          name: "小米全自动智能门锁",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2b87ae4a36beef69bb2018eb1f8bce9b.png",
          url: "https://www.mi.com/buy/detail?product_id=12790",
          price: "1799元",
        },
        {
          name: "小米全自动智能门锁",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2b87ae4a36beef69bb2018eb1f8bce9b.png",
          url: "https://www.mi.com/buy/detail?product_id=12790",
          price: "1799元",
        },
        {
          name: "小米全自动智能门锁",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2b87ae4a36beef69bb2018eb1f8bce9b.png",
          url: "https://www.mi.com/buy/detail?product_id=12790",
          price: "1799元",
        },
        {
          name: "小米全自动智能门锁",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2b87ae4a36beef69bb2018eb1f8bce9b.png",
          url: "https://www.mi.com/buy/detail?product_id=12790",
          price: "1799元",
        },
        {
          name: "小米全自动智能门锁",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2b87ae4a36beef69bb2018eb1f8bce9b.png",
          url: "https://www.mi.com/buy/detail?product_id=12790",
          price: "1799元",
        },
        {
          name: "小米全自动智能门锁",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2b87ae4a36beef69bb2018eb1f8bce9b.png",
          url: "https://www.mi.com/buy/detail?product_id=12790",
          price: "1799元",
        },
      ],
    };
  },
  methods: {
    showProduct(type) {
      if (type) {
        this.productStatus = true;
        this.currentType = this[type];
      }
      // this.productStatus = true
      clearTimeout(this.tids);
      // console.log(typeof type);
    },
    hideProduct() {
      let self = this;
      // 这里一定要设置一个定时器，这样可以使商品菜单在下落过程中有个缓冲过程，更容易控制显示变量，体验更好
      this.tids = setTimeout(function () {
        self.productStatus = false;
      }, 300);
    },
    evtIntFocus() {
      this.hotkeyStatus = true;
    },
    evtIntBlur() {
      this.hotkeyStatus = false;
    },
  },
};
</script>

<style scoped>
.contain {
  margin: 0 auto;
  width: 1226px;
  height: 100px;
}
.top-item {
  display: inline-block;
}
/* logo */
.header-logo {
  width: 62px;
  height: 100px;
  vertical-align: top;
}
.header-logo img {
  margin-top: 22px;

  width: 56px;
  height: 56px;
}
/* 导航栏 */
.header-nav {
  height: 100px;
  width: 850px;
}
.header-nav ul {
  width: 100%;
  height: 100px;
  margin: 0;
  padding: 12px 0 0 30px;
  font-size: 16px;
}
#J_navCategory {
  display: inline-block;
  width: 127px;
  padding: 15px;
  /* ??? */
  /* height: 88px; */
}
.nav-item {
  display: inline-block;
  height: 100%;
  font-size: 16px;
  line-height: 72px;
}
.nav-item span {
  padding: 0 10px;
  color: #333;
}
.nav-item span:hover {
  color: #ff6700;
}
/* 搜索框 */
.header-search {
  float: right;
  position: relative;
  width: 296px;
  height: 50px;
  margin-top: 25px;
  font-size: 24px;
}
/* .header-search form:hover{
    border-color: yellow;
  } */
.search-form {
  position: relative;
  width: 296px;
  height: 50px;
  z-index: 20;
}
/* .search-form input{

  } */

.header-search .search-input {
  float: left;
  width: 223px;
  z-index: 1;
  height: 48px;
  padding: 0 10px;
  font-size: 14px;
  line-height: 48px;
  border: 1px solid #e0e0e0;
}
.search-input::after {
  content: "\e67c";
  font-family: "iconfont";
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.header-search .search-button {
  content: "\e67c";
  float: left;
  height: 48px;
  width: 70px;
  border: 1px solid #e0e0e0;
}
.header-search .search-button:hover {
  background: #ff6700;
}
.hotkey {
  position: absolute;
  z-index: 99;
  border: 1px solid lavender;
  background: #fff;
}
.hotkey li {
  width: 223px;
  height: 35px;
  padding: 3px 0;
}
.hotkey li:hover {
  background: lavender;
}
.hotkey li a {
  margin-left: 15px;
  font-size: 15px;
  color: gray;
}

/* 商品展示 */
.show-product {
  position: absolute;
  top: 140px;
  width: 100%;
  height: 229px;
  border-top: 1px solid #e0e0e0;
  background: #fff;
  z-index: 3;
  box-shadow: 0 3px 4px rgba(0, 0, 0, 0.18);
}
.v-enter-active,
.v-leave-active {
  transition: all 0.3s ease;
  height: 229px;
}
.v-enter,
.v-leave-to {
  height: 0;
}
.product-item {
  position: relative;
  display: inline-block;
  padding: 35px 12px 0 12px;
  text-align: center;
  font-size: 12px;
}
.product-item i {
  position: absolute;
  left: 0;
  top: 35px;
  z-index: 10;
  width: 1px;
  height: 100px;
  background-color: #e0e0e0;
}

.product-img img {
  width: 160px;
  height: 110px;
  margin-bottom: 16px;
}
.product-text {
  color: #ff6700;
}
</style>