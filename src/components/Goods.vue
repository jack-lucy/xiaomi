<template>
  <div class="goods">
    <seckill></seckill>
    <phone></phone>
    <appliance></appliance>
  </div>
</template>

<script>
import Seckill from "./Goods/Seckill";
import Phone from "./Goods/Phone";
import Appliance from "./Goods/Appliance";
export default {
  components: {
    Seckill,
    Phone,
    Appliance,
  },
  name: "",
  data() {
    return {};
  },
};
</script>

<style scoped>
</style>