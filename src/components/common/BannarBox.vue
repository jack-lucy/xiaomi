<template>
  <div class="home-bannar-box">
    <a :href="bannarBox.url">
      <img :src="bannarBox.imgUrl" alt="">
    </a>
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
  props:{
    bannarBox:{
      type:Object,
      required: true
    }
  }
}
</script>

<style scoped>
.home-bannar-box{
  margin: 22px 0;
  width: 1226px;
  height: 120px;
}
img{
  width: 1226px;
  height: 120px;
}
</style>