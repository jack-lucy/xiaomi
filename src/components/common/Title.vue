<template>
  <div class="box-hd">
    <h2 class="title" v-text="title"></h2>
    <slot name="swiper-controls"></slot>
    <slot name="more"></slot>
    <slot name="category"></slot>
  </div>
</template>

<script>
export default {
  components:{
  
  }, 
  name:"",
  data() {
    return {
      
    }
  },
  props:["title"]
}
</script>

<style scoped>
.box-hd{
  width: 1226px;
  height: 58px;
}
.title{
    margin: 0;
    font-size: 22px;
    font-weight: 200;
    line-height: 58px;
    color: #333;
}
h2{
  float: left;
}
</style>