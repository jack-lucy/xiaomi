<template>
  <!-- 商品列表 -->
  <div class="banner-list" @mouseleave="hideProduct">
    <div class="list">
      <ul>
        <li v-for="item in typeList" @mouseenter="showProduct(item.type)">
          <a href="javascript:void(0);">{{ item.name }}</a>
          <em class="iconfont icon-you1"></em>
        </li>
      </ul>
    </div>
    <!-- 商品展示 -->
    <div class="prodcut-list" v-show="productStatus">
      <ul v-for="listItem in filterCurrGoods">
        <li v-for="item in listItem">
          <a :href="item.url">
            <img :src="item.imgUrl" alt="" />
            <span>{{ item.name }}</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {
      currentType: [],
      productStatus: false,
      typeList: [
        { type: "phone", name: "手机 电话卡" },
        { type: "tv", name: "电视 盒子" },
        { type: "lp", name: "笔记本 显示器" },
        { type: "appliance", name: "家电 插线器" },
        { type: "travel", name: "出行 穿戴" },
        { type: "intelligence", name: "智能 路由器" },
        { type: "source", name: "电源 配件" },
        { type: "health", name: "健康 儿童" },
        { type: "earphone", name: "耳机 音箱" },
        { type: "life", name: "生活 箱包" },
      ],
      phone: [
        {
          url: "https://www.mi.com/mixfold",
          imgUrl:
            "http://cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png",
          name: "小米MIX FOLD",
        },
        {
          url: "https://www.mi.com/mi11ultra",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png",
          name: "小米11 Ultra",
        },
        {
          url: "https://www.mi.com/mi11Pro",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/6cf44dfe89111cb35e1a2211481ff546.png",
          name: "小米11 Pro",
        },
        {
          url: "https://www.mi.com/mi11youth",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/72bd70039670d29610569421f753fcb6.png",
          name: "小米11 青春",
        },
        {
          url: "https://www.mi.com/mi10s",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/c89e7b3a3495acaa0a4df271d9da59ea.png",
          name: "小米10s",
        },
        {
          url: "https://www.mi.com/mi11",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a51c1afa4db8e47e62fad1f6fa4a8970.png",
          name: "小米11",
        },

        {
          url: "https://www.mi.com/buy/detail?product_id=10000214",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/4a7a4f24061860901f724b6ba6d75fd9.png",
          name: "小米10",
        },
      ],
      tv: [
        {
          url: "https://www.mi.com/buy/detail?product_id=13498",
          imgUrl:
            "http://cdn.cnbj1.fds.api.mi-img.com/mi-mall/9074723edc522839834f7fcd12b6f558.png",
          name: "Redmi Max”超大屏",
        },
      ],
      lp: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      appliance: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      travel: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      intelligence: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      source: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      health: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      earphone: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
      life: [
        {
          url: "https://www.mi.com/buy/detail?product_id=10000284",
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/32c652aa0d2da1d043b837eba6098541.png",
          name: "小米笔记本Pro 15",
        },
      ],
    };
  },
  computed: {
    filterCurrGoods: function () {
      let filterGoods = [[], [], [], [], []];
      this.currentType.forEach(function (item, index) {
        let goodsIndex = Math.floor(index / 6);
        filterGoods[goodsIndex].push(item);
      });
      return filterGoods;
    },
  },
  methods: {
    showProduct(type) {
      this.currentType = this[type];
      this.productStatus = true;
      // this.currentType = this[type]
    },
    hideProduct() {
      this.productStatus = false;
    },
  },
};
</script>

<style scoped>
.banner-list {
  position: absolute;
  top: 140px;
  left: 147px;
  /* 这里宽和高都不能写死哦，否则会把我们的轮播图覆盖掉 */
  /* left: 50%;
  margin-left: -613px;
  width: 1226px;
  height: 460px; */
  z-index: 3;
}
.list {
  /* display: inline-block; */
  float: left;
  width: 234px;
  height: 460px;
  font-size: 14px;
  color: #fff;
  background: rgba(105, 101, 101, 0.6);
}
.list ul {
  padding: 20px 0;
}
.list li {
  position: relative;
  width: 100%;
  height: 42px;
  line-height: 42px;
}
.list li:hover {
  background: #ff6700;
  cursor: pointer;
}
.list li a {
  padding-left: 30px;
  color: #fff;
}
.list li em {
  position: absolute;
  width: 16px;
  height: 16px;
  right: 20px;
  font-size: 16px;
  color: #e0e0e0;
}

/* 商品展示 */
.prodcut-list {
  float: left;
  /* width: 1000px; */
  /* display: flex;
	flex-flow: row nowrap;
	justify-content: flex-start; */
  height: 460px;
  background: #fff;
  box-shadow: 0 3px 4px rgba(0, 0, 0, 0.18);
  z-index: 99;
}
.prodcut-list ul {
  float: left;
  /* 注意：这里ul的宽不能写死，有多少商品就显示多少的ul */
  width: auto;
  height: 100%;
  padding: 2px 0;
}
.prodcut-list li {
  width: 265px;
  height: 76px;
}
.prodcut-list a {
  display: block;
  padding: 18px 20px;
}
.prodcut-list img {
  width: 40px;
  height: 40px;
  margin-right: 12px;
  float: left;
}
.prodcut-list a span {
  float: left;
  width: 172px;
  font-size: 14px;
  line-height: 40px;
  color: #000;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
.prodcut-list a span:hover {
  color: #ff6700;
}
</style>