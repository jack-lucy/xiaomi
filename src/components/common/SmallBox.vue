<template>
  <div class="small-box">
    <a href="https://www.mi.com/redmitv/98">
      <div class="figure-img">
        <img
          src="//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8861fafd390bf76f7446d4db2053560f.jpg?"
          alt=""
        />
      </div>
      <h3 class="title">Redmi智能电视MAX 98"</h3>
      <p class="price">
        <span class="num">1999</span>
        元
      </p>
    </a>
  </div>
</template>

<script>
export default {
  components: {},
  name: "",
  data() {
    return {};
  },
};
</script>

<style scoped>
.small-box {
  position: relative;
  display: inline-block;
  height: 143px;
  padding-top: 50px;
  width: 234px;
  margin-bottom: 14px;
  background: #fff;
  text-align: center;
  transition: all 0.3s;
}
.small-box:hover {
  transform: translateY(-1px);
  box-shadow: 5px 5px 20px #ccc;
}
.figure-img {
  display: inline-block;
  position: absolute;
  right: 20px;
  top: 32px;
}
.small-box img {
  width: 80px;
  height: 80px;
}
.title {
  margin: -10px 110px 5px 30px;
  font-size: 14px;
  color: #333;
  font-weight: 400;
}
.price {
  margin: 0 110px 0 30px;
  font-size: 12px;
  color: #ff6700;
}
</style>