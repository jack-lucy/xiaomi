<template>
  <!-- 商品展示 -->
  <div v-show="productStatus" class="show-product">
    <div class="contain">
      <ul>
        <li v-for="item in currentType" class="product-item">
          <a :href="item.src">
            <div class="product-img"><img :src="item.imgUrl" alt="" /></div>
            <div>{{ item.name }}</div>
            <div class="product-text">{{ item.price }}</div>
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
    return {};
  },
};
</script>

<style scoped>
</style>