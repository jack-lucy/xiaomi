<template>
  <div class="img-box">
    <a :href="imgBox.url">
      <img :src="imgBox.imgUrl" alt="">
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
  props:["imgBox"]
}
</script>

<style scoped>
.img-box{
  height: 300px;
  width: 234px;
  margin-bottom: 14px;
  transition: all 0.3s;
}
.img-box:hover{
  transform: translateY(-1px);
  box-shadow: 5px 5px 20px #ccc;
}
.img-box img{
    height: 300px;
  width: 234px;
}
</style>