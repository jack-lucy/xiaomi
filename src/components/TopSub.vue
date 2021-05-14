<template>
  <div class="home-hero-sub row">
    <div class="span4">
      <ul>
        <li v-for="(item, index) in information">
          <i class="topline"></i>
          <a :href="item.url">
            <img :src="item.imgUrl" alt="" />
            {{ item.name }}
          </a>
          <i class="leftline"></i>
        </li>
      </ul>
    </div>
    <div class="span16">
      <ul>
        <li v-for="(item, index) in information2">
          <a :href="item.url">
            <img :src="item.imgUrl" alt="" />
          </a>
        </li>
      </ul>
    </div>
    <!-- <div style="clear: both;"></div> -->
  </div>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {
      information: [
        {
          url: "https://www.mi.com/buy/seckill",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/82abdba456e8caaea5848a0cddce03db.png",
          name: "小米秒杀",
        },
        {
          url: "https://qiye.mi.com/",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/806f2dfb2d27978e33fe3815d3851fa3.png",
          name: "企业团购",
        },
        {
          url: "https://www.mi.com/order/fcode",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/eded6fa3b897a058163e2485532c4f10.png",
          name: "F码通道",
        },
        {
          url: "https://www.mi.com/mimobile",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/43a3195efa6a3cc7662efed8e7abe8bf.png",
          name: "米粉卡",
        },
        {
          url: "https://www.mi.com/a/h/16769.html",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/f4846bca6010a0deb9f85464409862af.png",
          name: "以旧换新",
        },
        {
          url: "https://account.xiaomi.com/",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/9a76d7636b08e0988efb4fc384ae497b.png",
          name: "话费充值",
        },
      ],
      information2: [
        {
          url: "https://www.mi.com/buy/detail?product_id=12511",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/5d4298059889417157e8492750328492.jpg",
        },
        {
          url: "https://www.mi.com/mi11",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/b30177d629bfbe2fb42251c1b8538f7b.jpg",
        },
        {
          url: "https://www.mi.com/buy/detail?product_id=12931",
          imgUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/793913688bfaee26b755a0b0cc8575fd.jpg",
        },
      ],
    };
  },
};
</script>

<style scoped>
/* 这里盒子的设计和官网有冲突  这里留下margin问题 */
.home-hero-sub {
  position: relative;
  margin: 14px 0 0 0;
  width: 1226px;
  height: 170px;
  left: 50%;
  transform: translate(-50%);
  text-align: center;
}
.span4 {
  float: left;
  width: 234px;
  height: 100%;
  /* margin-left: 14px; */
  background: #665e57;
}
.span4 ul {
  padding: 3px;
  width: 228px;
  height: 164px;
  font-size: 12px;
}
.span4 ul li {
  float: left;
  position: relative;
  width: 70px;
  height: 82px;
  padding: 0 3px;
}
.span4 .topline {
  position: absolute;
  top: -1px;
  left: 6px;
  width: 64px;
  height: 1px;
  background: rgba(255, 255, 255, 0.05);
}
.span4 .leftline {
  position: absolute;
  top: 6px;
  left: 0;
  width: 1px;
  height: 70px;
  background: rgba(255, 255, 255, 0.05);
}
.span4 a {
  width: 70px;
  height: 45.6px;
  padding-top: 18px;
  color: #fff;
}
.span4 img {
  width: 24px;
  height: 24px;
  margin: 18px 23px 4px 23px;
}
.span16 {
  float: left;
  width: 978px;
  height: 170px;
  margin-left: 14px;
}
.span16 li {
  float: left;
  width: 316px;
  height: 170px;
  transition: all 0.3s;
}
.span16 li:hover {
  /* transform: translateY(-1px); */
  box-shadow: 5px 5px 20px #ccc;
}
.span16 li:nth-child(2) {
  margin-left: 15px;
}
.span16 li:nth-child(3) {
  margin-left: 15px;
}
.span16 img {
  width: 316px;
  height: 170px;
}
</style>