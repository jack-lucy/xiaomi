<template>
  <div class="seckill">
    <Title :title="title">
      <!-- 使用组件插槽 添加左右按钮 -->
      <div class="swiper-controls" slot="swiper-controls">
        <span
          class="slidePre"
          @click="slidePre"
          @mouseenter="LchangeColor"
          @mouseleave="LbackColor"
        >
          <i class="iconfont icon-xiangzuo" ref="leftArrow"></i>
        </span>
        <span
          class="slideNext"
          @click="slideNext"
          @mouseenter="RchangeColor"
          @mouseleave="RbackColor"
        >
          <i class="iconfont icon-you1" ref="rightArrow"></i>
        </span>
      </div>
    </Title>
    <div class="contain">
      <time-box></time-box>
      <div class="right-box">
        <div class="scroll-area">
          <!-- 当我们遍历某个组件时，应适当的给其加上相应的key -->
          <seckill-box
            v-for="(item, index) in goods"
            :key="index"
            :goodsItem="item"
          ></seckill-box>
        </div>
      </div>
    </div>
    <bannar-box :bannarBox="bannarBox"></bannar-box>
  </div>
</template>

<script>
import Title from "../common/Title";
import TimeBox from "../common/TimeBox";
import SeckillBox from "../common/SeckillBox";
import BannarBox from "../common/BannarBox";
export default {
  components: {
    Title,
    TimeBox,
    SeckillBox,
    BannarBox,
  },
  name: "Seckill",
  data() {
    return {
      //节流阀控制
      flag: true,
      page: 0,
      swiperWidth: 992,
      title: "小米秒杀",
      goods: [
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e28062a48bc10078c7f3fe4cd1f0c442.png",
          name: "米家电动剃须刀 S700 黑色",
          desc: "陶瓷净须，开局之作*",
          price: 479,
          oldPrice: 499,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e28062a48bc10078c7f3fe4cd1f0c442.png",
          name: "米家电动剃须刀 S700 黑色",
          desc: "陶瓷净须，开局之作*",
          price: 479,
          oldPrice: 499,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e28062a48bc10078c7f3fe4cd1f0c442.png",
          name: "米家电动剃须刀 S700 黑色",
          desc: "陶瓷净须，开局之作*",
          price: 479,
          oldPrice: 499,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e28062a48bc10078c7f3fe4cd1f0c442.png",
          name: "米家电动剃须刀 S700 黑色",
          desc: "陶瓷净须，开局之作*",
          price: 479,
          oldPrice: 499,
        },

        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/16f33709f83b7e937953fbc8969468c8.png",
          name: "米家运动心电T恤 M 深花灰",
          desc: "米家运动心电T恤",
          price: 249,
          oldPrice: 299,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/16f33709f83b7e937953fbc8969468c8.png",
          name: "米米家运动心电T恤 M 深花灰",
          desc: "米家运动心电T恤",
          price: 249,
          oldPrice: 299,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/16f33709f83b7e937953fbc8969468c8.png",
          name: "米家运动心电T恤 M 深花灰",
          desc: "米家运动心电T恤",
          price: 249,
          oldPrice: 299,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/16f33709f83b7e937953fbc8969468c8.png",
          name: "米家运动心电T恤 M 深花灰",
          desc: "米家运动心电T恤",
          price: 249,
          oldPrice: 299,
        },

        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ba485f3f5e5e5e7ff2670afae1c648a7.png",
          name: "千年榫营造积木 祈年殿 白色",
          desc: "千年榫营造积木 祈年殿",
          price: 799,
          oldPrice: 999,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ba485f3f5e5e5e7ff2670afae1c648a7.png",
          name: "千年榫营造积木 祈年殿 白色",
          desc: "千年榫营造积木 祈年殿",
          price: 799,
          oldPrice: 999,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ba485f3f5e5e5e7ff2670afae1c648a7.png",
          name: "千年榫营造积木 祈年殿 白色",
          desc: "千年榫营造积木 祈年殿",
          price: 799,
          oldPrice: 999,
        },
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ba485f3f5e5e5e7ff2670afae1c648a7.png",
          name: "千年榫营造积木 祈年殿 白色",
          desc: "千年榫营造积木 祈年殿",
          price: 799,
          oldPrice: 999,
        },
      ],
      bannarBox: {
        url: "https://www.mi.com/redminote9",
        imgUrl:
          "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/431e5fd6bfd1b67d096928248be18303.jpg",
      },
    };
  },

  methods: {
    // 动画函数   这里的制作和轮播图思想一样
    animate(obj, target, callback) {
      clearInterval(obj.timer);
      obj.timer = setInterval(function () {
        var step = (target - obj.offsetLeft) / 10;
        step = step > 0 ? Math.ceil(step) : Math.floor(step);
        if (obj.offsetLeft === target) {
          clearInterval(obj.timer);
          callback && callback();
        }
        obj.style.left = obj.offsetLeft + step + "px";
      }, 15);
    },
    slidePre() {
      var ul = document.querySelector(".scroll-area");
      if (this.flag) {
        this.flag = false;
        if (this.page !== 0) {
          this.page--;
        }
        this.animate(ul, -this.page * this.swiperWidth, this.changeFlag());
      }
    },
    slideNext() {
      var ul = document.querySelector(".scroll-area");
      if (this.flag) {
        this.flag = false;
        if (this.page !== 2) {
          this.page++;
        }
        this.animate(ul, -this.page * this.swiperWidth, this.changeFlag());
        console.log(this.page);
      }
    },
    changeFlag() {
      this.flag = true;
    },

    // 左右按钮放入和离开颜色变换
    LchangeColor() {
      if (this.page !== 0) {
        this.$refs.leftArrow.style = "color:#ff6709;";
      }
    },
    LbackColor() {
      this.$refs.leftArrow.style = "color:e0e0e0;";
    },
    RchangeColor() {
      if (this.page !== 2) {
        this.$refs.rightArrow.style = "color:#ff6709;";
      }
    },
    RbackColor() {
      this.$refs.rightArrow.style = "color:e0e0e0;";
    },
  },
  // 很尴尬，这里会被前面的方法覆盖掉???
  mounted() {
    if (this.page === 0) {
      this.$refs.leftArrow.style = "color:e0e0e0;";
    }
    if (this.page === 2) {
      this.$refs.rightArrow.style = "color:e0e0e0;";
    }
  },
};
</script>

<style scoped>
.seckill {
  width: 1226px;
  height: 562px;
}
.contain {
  height: 340px;
}
.swiper-controls {
  float: right;
  line-height: 58px;
}
.swiper-controls span {
  display: inline-block;
  width: 24px;
  height: 20px;
  margin-left: -4px;
  border: 1px solid #e0e0e0;
  font-size: 16px;
  line-height: 20px;
  text-align: center;
}
.right-box {
  /* 相对定位可以和浮动一起使用 */
  /* 在设置滚动的时候，我们使用子绝父相的定位模式 */
  position: relative;
  float: left;
  width: 992px;
  height: 100%;
  overflow: hidden;
  /* background: blue; */
}
.scroll-area {
  position: absolute;
  width: 300%;
  height: 100%;
  /* background: pink; */
}
</style>