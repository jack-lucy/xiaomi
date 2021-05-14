<template>
  <div class="seckill-box">
    <a :href="goodsItem.url">
      <div class="content">
        <div class="thumb">
          <img :src="goodsItem.imgUrl" alt="">
        </div>
        <h3 class="title">{{goodsItem.name}}</h3>
        <p class="desc">{{goodsItem.desc}}</p>
        <p class="price">
          <span>{{goodsItem.price}}</span>
          元
          <del>{{goodsItem.oldPrice}}</del>
        </p>
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
  props:{
    goodsItem:{
      type:Object
    }
  }
}
</script>

<style scoped>
.seckill-box{
  float: left;
  width: 234px;
  height: 340px;
  border-top: 1px;
  margin-left: 14px;
  background: #fff;
  text-align: center;
}
.content{
  width: 234px;
  height: 262.2px;
  margin-top: 39px;
}
.thumb{
  margin: 0 37px;
  margin-bottom: 22px;
  width: 160px;
  height: 165.6px;
}
.thumb img{
  width: 160px;
  height: 160px;
}
.title{
  margin: 0 20px 3px;
  font-size: 14px;
  font-weight: 400;
  text-overflow: ellipsis;
  color: #212121;
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
.price del{
  color: #b0b0b0;
}
</style>