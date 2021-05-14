<template>
  <div class="appliance">
    <Title :title="title">
      <div slot="category" class="category">
        <span class="hot" ref="hot" @mouseenter="backOne">热门</span>
        <span class="tv" ref="tv" @mouseenter="backTwo">电视影音</span>
      </div>
    </Title>
    <div class="contain">
      <div class="float-box left">
        <img-box
          v-for="(item, index) in imgBox"
          :key="index"
          :imgBox="item"
          class="box"
        ></img-box>
      </div>
      <!-- 这里其实有两个区域，通过flag控制 -->
      <div class="float-box right" v-if="flag === 1">
        <middle-box
          v-for="(item, index) in goodsItem"
          :key="index"
          :goodsItem="item"
          class="goodsItem"
        ></middle-box>
        <div class="goodsItem andBox">
          <small-box class="float-smallBox"></small-box>
          <more-box class="float-smallBox"></more-box>
        </div>
      </div>
      <div class="float-box right" v-else>
        <middle-box
          v-for="(item, index) in tv"
          :key="index"
          :goodsItem="item"
          class="goodsItem"
        ></middle-box>
        <div class="goodsItem andBox">
          <small-box class="float-smallBox"></small-box>
          <more-box class="float-smallBox"></more-box>
        </div>
      </div>
    </div>
    <bannar-box :bannarBox="bannarBox"></bannar-box>
  </div>
</template>

<script>
import Title from "../common/Title";
import ImgBox from "../common/ImgBox";
import MiddleBox from "../common/MiddleBox";
import SmallBox from "../common/SmallBox";
import MoreBox from "../common/MoreBox";
import BannarBox from "../common/BannarBox";

export default {
  components: {
    Title,
    ImgBox,
    MiddleBox,
    SmallBox,
    MoreBox,
    BannarBox,
  },

  data() {
    return {
      flag: 1,
      title: "家电",
      imgBox: [
        {
          url: "https://www.mi.com/redmitv/98",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/116fc43816b87192be4e67cf762e8da5.jpeg",
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=11843",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/dfbdabe36b2d630d57a015e6fb5eb3ea.jpg",
        },
      ],
      goodsItem: [
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
        {
          url: "https://www.mi.com/buy?product_id=12849",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/03a9e7e96a09d256ca1badeec186c859.jpg",
          name: "小米全面屏电视65英寸 E65X",
          desc: "全面屏设计",
          price: 3199,
          oldPrice: 3299,
        },
      ],
      tv: [
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12045",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/20d36fbaa18625e4fe507af31e4e9f83.jpg",
          name: "全面屏电视E43K",
          desc: "全面屏设计，海量内容",
          price: 1499,
          oldPrice: 1599,
        },
      ],
      bannarBox: {
        url: "https://www.mi.com/buy/detail?product_id=10025",
        imgUrl:
          "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/59e8fc8ba9718c266882719fb4bbcedd.jpg",
      },
    };
  },
  methods: {
    backOne() {
      this.flag = 1;
      if (this.flag === 1) {
        this.$refs.hot.style =
          "border-bottom: 2px solid #ff6709;color: #ff6709;";
        this.$refs.tv.style = "color: #000;";
      }
    },
    backTwo() {
      this.flag = 2;
      if (this.flag === 2) {
        this.$refs.tv.style =
          "border-bottom: 2px solid #ff6709;color: #ff6709;";
        this.$refs.hot.style = "color: #000;";
      }
    },
  },
  mounted() {
    if (this.flag === 1) {
      this.$refs.hot.style = "border-bottom: 2px solid #ff6709;color: #ff6709;";
    }
  },
};
</script>

<style scoped>
.appliance {
  width: 1226px;
  height: 850px;
  margin-bottom: 8px;
}
.category {
  float: right;
  line-height: 58px;
}
.category span {
  padding: 5px 5px;
  font-size: 16px;
  cursor: pointer;
}
.contain {
  width: 1226px;
  height: 628px;
  margin-bottom: 8px;
}
.float-box {
  float: left;
}
.left {
  width: 234px;
  height: 628px;
}
.right {
  /* 这里根据盒子的排布，需要计算盒子的大小。 */
  width: 992px;
  height: 628px;
}
.goodsItem {
  float: left;
}
.andBox {
  width: 234px;
  height: 300px;
  margin-left: 14px;
  margin-bottom: 14px;
  /* padding: 20px 0; */
  /* background: #fff; */
  text-align: center;
}
.float-smallBox {
  float: left;
}
</style>