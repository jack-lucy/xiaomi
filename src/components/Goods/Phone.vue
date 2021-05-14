<template>
  <div class="home-brick-box">
    <Title :title="title">
      <div slot="more" class="more">
        <a href="https://www.mi.com/p/1915.html">
          查看更多
          <i class="iconfont icon-you2"></i>
        </a>
      </div>
    </Title>
    <div class="contain">
      <big-box class="box-float left"></big-box>
      <div class="box-float right">
        <middle-box
          v-for="(item, index) in goodsItem"
          :key="index"
          :goodsItem="item"
          class="goodsItem"
        ></middle-box>
        <!-- <div style="clear: both;"></div> -->
      </div>
    </div>
    <bannar-box :bannarBox="bannarBox"></bannar-box>
  </div>
</template>

<script>
import Title from "../common/Title";
import BigBox from "../common/BigBox";
import MiddleBox from "../common/MiddleBox";
import BannarBox from "../common/BannarBox";
export default {
  components: {
    Title,
    BigBox,
    MiddleBox,
    BannarBox,
  },
  name: "",
  data() {
    return {
      title: "手机",
      goodsItem: [
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/5dc32ec73299ff79556dcd1cf0f0ac11.png",
          name: "小米MIX FOLD",
          desc: "折叠大屏｜自研芯片",
          price: 9999,
        },
      ],
      bannarBox: {
        url: "https://www.mi.com/a/h/15707.html",
        imgUrl:
          "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/41d16e66381cfeda7b6b39ab67678d5e.jpg",
      },
    };
  },
};
</script>

<style scoped>
.home-brick-box {
  width: 1226px;
  height: 850px;
  margin-bottom: 8px;
}
.contain {
  width: 1226px;
  height: 628px;
}
.box-float {
  float: left;
}
.right {
  /* 这里一定要设置宽度？？ */
  width: 992px;
  height: 100%;
}
.goodsItem {
  float: left;
}
.more {
  float: right;
  line-height: 58px;
}
.more i,
.more a {
  font-size: 16px;
  color: #424242;
}
/* 这里设计有问题 */
.more a:hover,
.more i:hover {
  color: #ff6700;
}
</style>