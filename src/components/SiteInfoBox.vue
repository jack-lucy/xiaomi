<template>
  <div class="site-info">
    <div class="contain">
      <!-- 图标 -->
      <div class="logo ir">小米官网</div>
      <!-- 小链接 -->
      <div class="info-text">
        <p class="sites">
          <span v-for="item in info1">
            <a :href="item.url">{{ item.name }}</a>
            <span>|</span>
          </span>
        </p>
        <p class="sites">
          <span v-for="item in info2">
            <a :href="item.url">{{ item.name }}</a>
            <span>|</span>
          </span>
        </p>
        <p class="font-color">
          ©
          <a href="">mi.com</a>
          京ICP证110507号
          <a href="">京ICP备10046444号</a>
          <a href="">京公网安备11010802020134号</a><br />
          <a href="">（京）网械平台备字（2018）第00005号</a>
          <a href="">互联网药品信息服务资格证 (京)-非经营性-2014-0090</a>
          <a href="">营业执照</a>
          <a href="">医疗器械质量公告</a><br />
          <a href="">增值电信业务许可证</a>
          <a href=""> 网络食品经营备案 京食药网食备202010048</a>
          <a href="">食品经营许可证</a><br />
          违法和不良信息举报电话：171-5104-4404
          <a href="">知识产权侵权投诉</a>
          &nbsp;本网站所列数据，除特殊说明，所有数据均出自我司实验室测试
        </p>
      </div>
      <!-- 各种认证 -->
      <div class="info-links">
        <a v-for="item in info3" :href="item.url">
          <img :src="item.imgUrl" alt="" />
        </a>
      </div>
    </div>
    <div class="slogan ir">探索黑科技，小米为发烧而生</div>
  </div>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {
      info1: [
        { url: "//www.mi.com/index.html", name: "小米商城" },
        { url: "//www.mi.com/index.html", name: "MIUI" },
        { url: "//www.mi.com/index.html", name: "米家" },
        { url: "//www.mi.com/index.html", name: "米聊" },
        { url: "//www.mi.com/index.html", name: "多看" },
        { url: "//www.mi.com/index.html", name: " 游戏" },
        { url: "//www.mi.com/index.html", name: "政坛服务" },
        { url: "//www.mi.com/index.html", name: "小米天猫店" },
        { url: "//www.mi.com/index.html", name: "小米集团隐私政策" },
        { url: "//www.mi.com/index.html", name: "小米公司儿童信息保护规则" },
        { url: "//www.mi.com/index.html", name: "小米商城隐私政策" },
        { url: "//www.mi.com/index.html", name: "小米商城用户协议" },
        { url: "//www.mi.com/index.html", name: "问题反馈" },
        { url: "//www.mi.com/index.html", name: "Select Location" },
      ],
      info2: [
        {
          url: "//www.mi.com/index.html",
          name: "北京互联网法院法律服务工作站",
        },
        { url: "//www.mi.com/index.html", name: "中国消费者协会" },
        { url: "//www.mi.com/index.html", name: "北京市消费者协会" },
      ],
      info3: [
        {
          url:
            "https://privacy.truste.com/privacy-seal/validation?rid=4fc28a8c-6822-4980-9c4b-9fdc69b94eb8&lang=zh-cn",
          imgUrl: "//i1.mifile.cn/f/i/17/site/truste.png",
        },
        {
          url: "https://credit.cecdc.com/CX20120926001783002010.html",
          imgUrl: "//s01.mifile.cn/i/v-logo-2.png",
        },
        {
          url:
            "https://xyt.xinchacha.com/pcinfo?sn=523009637759455232&certType=6",
          imgUrl: "//xyt.xinchacha.com/img/icon/icon3.png",
        },
        {
          url: "https://www.mi.com/service/buy/commitment",
          imgUrl:
            "//i8.mifile.cn/b2c-mimall-media/ba10428a4f9495ac310fd0b5e0cf8370.png",
        },
        {
          url:
            "https://webcert.cnmstl.net/cert/grade?sn=3af21034e35011eab3ea00163e068ceb",
          imgUrl:
            "https://cnbj1.fds.api.xiaomi.com/b2c-misite-activity/f1ee261b96ae71e845efba398efeca02.png",
        },
      ],
    };
  },
};
</script>

<style scoped>
.site-info {
  padding: 30px 0;
  font-size: 12px;
  background: #fafafa;
}
.contain {
  position: relative;
  width: 1226px;
  margin-right: auto;
  margin-left: auto;
}
.contain::before {
  content: "";
  display: table;
}
.contain::after {
  content: "";
  display: table;
}
.site-info .logo {
  width: 56px;
  height: 56px;
  margin-right: 10px;
  background: url(//s02.mifile.cn/assets/static/image/logo-mi2.png) no-repeat;
  background-size: 56px;
  position: absolute;
  top: 0;
  left: 0;
}
.site-info .info-text {
  color: #b0b0b0;
  padding-left: 67px;
}
.site-info .info-text p {
  margin: 0;
  line-height: 18px;
}
.info-text .sites a {
  color: #757575;
  font-size: 12px;
}
.info-text .sites a:hover {
  color: #ff6700;
}

.info-text .font-color a {
  color: #b0b0b0;
}
.info-text .font-color a:hover {
  color: #ff6700;
}

.info-links {
  height: 28px;
  margin: 4px 0 15px;
  padding-left: 67px;
}
.info-links img {
  width: auto;
  height: 28px;
}
.site-info .slogan {
  clear: both;
  margin: 30px auto 0;
  width: 100%;
  height: 19px;
  background: url(https://cdn.cnbj1.fds.api.mi-img.com/staticsfile/global/slogan2020.png)
    no-repeat center 0;
}
.ir {
  display: block;
  text-align: left;
  text-indent: -9999em;
  overflow: hidden;
}
</style>