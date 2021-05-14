<template>
  <!-- 小米服务版块 -->
  <div class="site-footer">
    <div class="contain">
      <div class="footer-service">
        <ul>
          <li v-for="item in serverInfo">
            <a :href="item.url">
              <i class="iconfont" :class="item.iconfont"></i>
              <span>{{ item.name }}</span>
            </a>
          </li>
        </ul>
      </div>
      <!-- vue双重for循环 -->
      <div class="footer-links">
        <dl v-for="item in footerLinsInfo">
          <dt>{{ item.name }}</dt>
          <dd v-for="item1 in item.info">
            <a :href="item1.url">{{ item1.name }}</a>
          </dd>
        </dl>
        <div class="col-contact">
          <p class="phone">400-100-5678</p>
          <p>8:00-18:00（仅收市话费）</p>
          <a href="" class="btn">
            <span> 人工客服 </span>
          </a>
          <div class="follow">
            关注小米：
            <a href="https://weibo.com/xiaomishangcheng" class="wb"></a>
            <a
              href="javascript:void(0);"
              class="wx"
              ref="wx"
              @mouseenter="showCode"
              @mouseleave="hideCode"
            ></a>
            <img
              src="//cdn.cnbj1.fds.api.mi-img.com/staticsfile/global/wx-img.png"
              alt=""
              id="J_followWxImg"
              v-show="codeFlag"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {
      codeFlag: false,
      serverInfo: [
        {
          url: "https://www.mi.com/service/quick-repair",
          name: "预约维修服务",
          iconfont: "icon-editor2",
        },
        {
          url: "https://www.mi.com/service/exchange#back",
          name: "7天无理由退货",
          iconfont: "icon-7tiantuihuanhuo",
        },
        {
          url: "https://www.mi.com/service/exchange#back",
          name: "15天免费换货",
          iconfont: "icon-15tianwuliyoutuihuo",
        },
        {
          url: "https://www.mi.com/service/buy/Postal%20policy",
          name: "满69包邮",
          iconfont: "icon-liwu",
        },
        {
          url: "https://www.mi.com/service/sitelist",
          name: "520家售后网点",
          iconfont: "icon-icon-test",
        },
      ],
      footerLinsInfo: [
        {
          name: "帮助中心",
          info: [
            {
              url: "https://www.mi.com/service/account/Account%20registration",
              name: "账户管理",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
          ],
        },
        {
          name: "服务支持",
          info: [
            {
              url: "https://www.mi.com/service/account/Account%20registration",
              name: "账户管理",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
          ],
        },
        {
          name: "线下门店",
          info: [
            {
              url: "https://www.mi.com/service/account/Account%20registration",
              name: "账户管理",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
          ],
        },
        {
          name: "关于小米",
          info: [
            {
              url: "https://www.mi.com/service/account/Account%20registration",
              name: "账户管理",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
          ],
        },
        {
          name: "关于我们",
          info: [
            {
              url: "https://www.mi.com/service/account/Account%20registration",
              name: "账户管理",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
          ],
        },
        {
          name: "特色服务",
          info: [
            {
              url: "https://www.mi.com/service/account/Account%20registration",
              name: "账户管理",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
            {
              url: "https://www.mi.com/service/buy/SalesTime",
              name: "购物指南",
            },
          ],
        },
      ],
    };
  },
  methods: {
    showCode() {
      this.codeFlag = true;
    },
    hideCode() {
      this.codeFlag = false;
    },
  },
};
</script>

<style scoped>
.contain {
  width: 1226px;
  margin: 0 auto;
}
/* 使用伪元素达到清除浮动的效果 */
/* .contain::before{
    content: "";
    display: table;
    clear: both;
}
.contain:after {
    content: " ";
    display: table;
    clear: both;
} */
/* 服务区域 */
.footer-service {
  padding: 27px 0;
  border-bottom: 1px solid #e0e0e0;
}
/* .footer-service a:hover{
  color: #ff6700;
} */
.footer-service ul {
  height: 25px;
  width: 100%;
}
.footer-service li {
  float: left;
  width: 19.8%;
  height: 25px;
  border-left: 1px solid #e0e0e0;
  font-size: 16px;
  line-height: 25px;
  text-align: center;
}
.footer-service li span {
  color: #616161;
}
.footer-service li span:hover {
  color: #ff6700;
}
/* .footer-service a{
  &:hover{
    a , span{
    color: #ff6700;  
    }
  }
} */

.iconfont {
  margin-right: 6px;
  font-size: 24px;
  line-height: 24px;
  vertical-align: -4px;
  color: #000;
}
/* 详细链接区域 */
.footer-links {
  padding: 40px 0;
}
.footer-links::before {
  content: "";
  display: table;
  clear: both;
}
.footer-links::after {
  content: "";
  display: table;
  clear: both;
}
.footer-links dl {
  float: left;
  width: 160px;
  margin: 0;
}
.footer-links dt {
  margin: -1px 0 26px;
  font-size: 14px;
  line-height: 1.25;
  color: #424242;
}
.footer-links dd {
  margin: 10px 0 0;
  font-size: 12px;
}
.footer-links dd a {
  color: #757575;
}
.footer-links dd a:hover {
  color: #ff6700;
}
/* 人工客服区域 */
.col-contact {
  float: right;
  position: relative;
  width: 251px;
  border-left: 1px solid #e0e0e0;
  text-align: center;
  color: #616161;
}
.col-contact p {
  margin: 0 0 5px 0;
  font-size: 12px;
}
.col-contact .phone {
  font-size: 22px;
  line-height: 1;
  color: #ff6700;
}
.col-contact .btn {
  width: 118px;
  height: 28px;
  font-size: 12px;
  line-height: 28px;
  text-align: center;
  border: 1px solid #b0b0b0;
  border-color: #ff6700;
  background: #fff;
  color: #ff6700;
}
.col-contact .follow {
  font-size: 12px;
  margin-top: 10px;
  position: relative;
}
.col-contact a {
  width: 24px;
  height: 24px;
  display: inline-block;
  vertical-align: middle;
  margin-left: 6px;
  margin-top: -3px;
}
.col-contact .wb {
  background: url(https://cdn.cnbj1.fds.api.mi-img.com/staticsfile/global/wb.png)
    50% 0 no-repeat;
  background-size: cover;
}
.col-contact .wx {
  background: url(https://cdn.cnbj1.fds.api.mi-img.com/staticsfile/global/wx.png)
    50% 0 no-repeat;
  background-size: cover;
}
#J_followWxImg {
  position: absolute;
  width: 126px;
  height: 126px;
  z-index: 2;
  position: absolute;
  top: 20px;
  left: 100px;
}
</style>