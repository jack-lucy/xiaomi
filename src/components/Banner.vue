<template>
  <div>
    <div class="contain">
      <swiper :banners="banners"></swiper>
      <!-- <slide :banners="banners"></slide> -->
      <!-- <low-swiper :banners="banners"></low-swiper> -->
    </div>
  </div>
</template>

<script>
import Swiper from "./common/Swiper";
import Slide from "./common/Slide";
import lowSwiper from "./common/lowSwiper";
export default {
  components: {
    Swiper,
    Slide,
    lowSwiper,
  },
  name: "",
  data() {
    return {
      banners: [
        {
          sourceUrl: "//item.mi.com/buyphone/mi5",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/d8471a80a7dea49a3889386c16ebdc12.jpg",
        },
        {
          sourceUrl: "//item.mi.com/buyphone/hongmi3s",
          imgUrl: "http://i3.mifile.cn/a4/ba4939c9-fc0a-4916-bddc-726fa00f7e9b",
        },
        {
          sourceUrl: "//item.mi.com/buyphone/mimax",
          imgUrl: "http://i3.mifile.cn/a4/9ced2c9e-f685-4918-9b2a-402af2d2039f",
        },
        {
          sourceUrl: "//item.mi.com/buyphone/note3",
          imgUrl: "http://i3.mifile.cn/a4/f4bee59d-85a5-498f-ae57-a2cabe6aeb5b",
        },
        {
          sourceUrl: "//item.mi.com/buymitv/48",
          imgUrl: "http://i3.mifile.cn/a4/98fc8a58-c35c-475e-89cb-b8fe1659817f",
        },
      ],
    };
  },
};
</script>

<style scoped>
.contain {
  margin: 0 auto;
  width: 1226px;
  height: 460px;
}
</style>