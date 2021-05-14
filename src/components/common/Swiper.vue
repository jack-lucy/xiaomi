<template>
  <div class="swiper" @mouseenter="enterSwiper" @mouseleave="leaveSwiper">
    <span
      @click="slidePre"
      class="iconfont icon-xiangzuo slide-pre arrow"
    ></span>
    <span @click="slideNext" class="iconfont icon-you1 slide-next arrow"></span>
    <ul ref="imgUl" class="imgUl">
      <li v-for="item in banners">
        <a :href="item.sourceUrl">
          <img :src="item.imgUrl" alt="" />
        </a>
      </li>
      <li>
        <a href="//item.mi.com/buyphone/mi5"
          ><img
            src="http://i3.mifile.cn/a4/bc62a28f-de64-4eee-853b-36772a97f67e"
            alt=""
        /></a>
      </li>
    </ul>
    <ol class="circle">
      <li
        v-for="(item, index) in banners"
        :class="{ bg: index === 0 }"
        @click="clickDot(index)"
      ></li>
    </ol>
  </div>
</template>

<script>
/**
 * 缓动动画原理：
 * 1.让盒子每次移动的距离变小，速度就会慢慢地停下来
 * 2.核心算法：（目标值-现在的位置）/10  作为每次移动的距离
 * 3.当前盒子位置等于目标值的时候停止定时器
 */
export default {
  components: {},
  name: "",
  props: {
    banners: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      // 节流阀标志
      flag: true,
      //当前图片索引
      page: 0,
      //当前小点索引
      circle: 0,
      //轮播图大小
      swiperWidth: 1226,
      //轮播图定时器时间
      time: 3000,
      //定时器
      timer: null,
    };
  },
  mounted() {
    this.timer = setInterval(this.slideNext, this.time);
    console.log(this.timer);
  },
  beforeDestroy() {
    clearInterval(this.timer);
  },
  methods: {
    // 动画函数
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

    //鼠标停留在轮播图区域，显示左右按钮，清除定时器
    enterSwiper() {
      var preClick = document.querySelector(".slide-pre");
      var nextClick = document.querySelector(".slide-next");
      preClick.style.display = "block";
      nextClick.style.display = "block";
      clearInterval(this.timer);
      this.timer = null;
    },
    //鼠标离开在轮播图区域，隐藏左右按钮，恢复定时器
    leaveSwiper() {
      var preClick = document.querySelector(".slide-pre");
      var nextClick = document.querySelector(".slide-next");
      preClick.style.display = "none";
      nextClick.style.display = "none";
      this.timer = setInterval(this.slideNext, this.time);
      console.log(this.timer);
    },
    //1.点击左侧按钮，如果为第一张图片，那么将当前图片索引快速转化为最后一张（即我们复制的第一张图片），并将ul移动相应距离，这个过程执行很快，几乎无法捕抓。 2.然后将当前图片索引--，执行缓动动画函数，同时改变相应的小点索引。
    slidePre() {
      var ul = document.querySelector(".imgUl");
      var ol = document.querySelector(".circle");
      if (this.flag) {
        this.flag = false;
        if (this.page === 0) {
          this.page = ul.children.length - 1;
          ul.style.left = -this.page * this.swiperWidth + "px";
        }
        this.page--;
        this.animate(ul, -this.page * this.swiperWidth, this.changeFlag());
        this.circle--;
        this.circle = this.circle < 0 ? ol.children.length - 1 : this.circle;
        this.changeDot(this.circle);
      }
    },
    slideNext() {
      var ul = document.querySelector(".imgUl");
      var ol = document.querySelector(".circle");
      if (this.flag) {
        this.flag = false;
        if (this.page === ul.children.length - 1) {
          ul.style.left = 0;
          this.page = 0;
        }
        this.page++;
        this.animate(ul, -this.page * this.swiperWidth, this.changeFlag());
        this.circle++;
        this.circle = this.circle > ol.children.length - 1 ? 0 : this.circle;
        this.changeDot(this.circle);
      }
    },

    // 点击小圆圈，跳转到相应的图片
    clickDot(index) {
      var ul = document.querySelector(".imgUl");
      var ol = document.querySelector("ol");
      for (var i = 0; i < ol.children.length; i++) {
        ol.children[i].style = "background:darkslategray;";
      }
      ol.children[index].style = "background:orange;";
      this.animate(ul, -index * this.swiperWidth);
    },
    //图片跳转，改变相应的小点
    changeDot(index) {
      var ol = document.querySelector("ol");
      for (var i = 0; i < ol.children.length; i++) {
        ol.children[i].style = "background:darkslategray;";
      }
      ol.children[index].style = "background:orange;";
    },
    // 节流阀控制
    changeFlag() {
      this.flag = true;
    },
    changeRed(index) {
      var ol = document.querySelector("ol");
      ol.children[index].style = "background:red;";
    },
    changeBack(index) {
      var ol = document.querySelector("ol");
      ol.children[index].style = "background:darkslategray;";
    },
  },
};
</script>

<style scoped>
/* 使用子绝父相的定位模式 */
.swiper {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.swiper ul {
  position: absolute;
  top: 0;
  left: 0;
  /* 这里的宽度至少必须是轮播图片+1的宽度*/
  width: 600%;
}
.swiper ul li {
  float: left;
}
/* 这里图片的宽高得根据轮播图大小设定 */
.swiper ul li a img {
  width: 1226px;
  height: 460px;
}
.arrow {
  display: none;
  position: absolute;
  top: 50%;
  margin-top: -10px;
  width: 41px;
  height: 69px;
  line-height: 69px;
  font-size: 30px;
  background: rgba(0, 0, 0, 0.3);
  z-index: 99;
}
.slide-pre {
  left: 234px;
}
.slide-next {
  right: 0;
}
.circle {
  position: absolute;
  left: 50%;
  bottom: 15px;
  margin-left: -90px;
  width: 180px;
  height: 12px;
  background: rgba(255, 255, 255, 0.4);
  border-radius: 8px;
  /* z-index: 5; */
}
.circle li {
  float: left;
  width: 30px;
  height: 5px;
  background: darkslategray;
  margin: 3px;
}
.circle li:hover {
  background: red;
}
.circle .bg {
  background: orange;
}
</style>