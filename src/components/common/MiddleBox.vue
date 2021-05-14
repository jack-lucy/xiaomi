<template>
  <div class="span16">
    <a :href="goodsItem.url">
      <div class="figure-img">
        <img :src="goodsItem.imgUrl" alt="">
      </div>
      <h3 class="title">{{goodsItem.name}}</h3>
        <p class="desc">{{goodsItem.desc}}</p>
        <p class="price">
          <span class="num">{{goodsItem.price}}</span>
          元
          <span>起</span>
        </p>
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
    goodsItem:{
      type:Object
    }
  }
}
</script>

<style scoped>
.span16{
  width: 234px;
  height: 300px;
  margin-left: 14px;
  margin-bottom: 14px;
  padding: 20px 0;
  background: #fff;
  text-align: center;
  transition: all 0.3s;
}
.span16:hover{
  transform: translateY(-1px);
  box-shadow: 5px 5px 20px #ccc;
}
.figure-img{
  width: 160px;
  height: 160px;
  margin: 0 37px;
  margin-bottom: 18px;
}
.figure-img img{
  width: 160px;
  height: 160px;
}
.title{
  margin: 0 10px 2px;
  font-size: 14px;
  font-weight: 400;
  text-overflow: ellipsis;
  color: #333;
  overflow: hidden;
  white-space: nowrap;
}
.desc{
      height: 18px;
    margin: 0 20px 12px;
    font-size: 12px;
    text-overflow: ellipsis;
    color: #b0b0b0;
    overflow: hidden;
    white-space: nowrap;
}
.price{
    margin: 0;
    color: #ff6709;
}

</style>