<template>
  <div class="more-box">
    <a href="">
      <div class="more">
        浏览更多
        <small>热门</small>
      </div>
      <div class="figure-img">
        <i class="iconfont icon-you"></i>
      </div>
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
}
</script>

<style scoped>
.more-box{
  position: relative;
  display: inline-block;
  height: 143px;
  padding-top: 50px;
  width: 234px;
  text-align: left;
  margin-bottom: 14px;
  background: #fff;
  transition: all .3s;
}
.more-box:hover{
  transform: translateY(-1px);
  box-shadow: 5px 5px 20px #ccc;
}
.more{
  display: block;
  margin: 0 110px 0 30px;
  font-size: 18px;
  color: #333;
}
.more small{
  display: block;
  font-size: 12px;
  color: #757575;
}
.figure-img i{
  position: absolute;
  left: 140px;
  top: 50px;
  font-weight: 1000;
  font-size: 48px;  
  line-height: 48px;
  color: #ff6700;
}
</style>