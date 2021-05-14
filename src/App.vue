<template>
  <div>
    <!-- 版心区域 -->
    <top-bar></top-bar>
    <top-header></top-header>
    <div class="bannar">
      <div class="contain">
        <banner></banner>
        <top-sub></top-sub>
      </div>
    </div>
    <!-- 详细商品区域 -->
    <div class="detail">
      <div class="contain">
        <goods></goods>
        <Video></Video>
      </div>
    </div>
    <footer-box></footer-box>
    <site-info-box></site-info-box>
    <tool-bar></tool-bar>
  </div>
</template>

<script>
/**bug：
 * 1.过渡动画，图片bug
 * 2.轮播图小点hover的bug
 */
import TopBar from "./components/TopBar";
import TopHeader from "./components/TopHeader";
import Banner from "./components/Banner";
import TopSub from "./components/TopSub";
import Goods from "./components/Goods";
import Video from "./components/Video";
import FooterBox from "./components/FooterBox";
import SiteInfoBox from "./components/SiteInfoBox";
import ToolBar from "./components/ToolBar";

export default {
  components: {
    TopBar,
    TopHeader,
    Banner,
    TopSub,
    Goods,
    Video,
    FooterBox,
    SiteInfoBox,
    ToolBar,
  },
  name: "App",
};
</script>

<style>
@import url("./assets/css/base.css");
.bannar {
  margin-bottom: 26px;
}
.contain {
  margin: 0 auto;
  width: 1226px;
}
.detail {
  background: #f5f5f5;
  padding-top: 4px;
  padding-bottom: 12px;
}
</style>

