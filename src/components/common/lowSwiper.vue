<template>
   <div class="slidershow middle">
      <div class="slides">
        <input v-for="(item,index) in banners" type="radio" name="r" :id="'r'+index">
        <div v-for="(item,index) in banners" :class="getClass(index)" class="slide">
          <img :src="item.imgUrl" alt="">
        </div>
      </div>

      <div class="navigation">
        <label v-for="(item,index) in banners" :for="'r'+index" class="bar"></label>
      </div>
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
    banners: {
			type: Array,
      required: true
		}
  },
  methods:{
    getClass(index){
      if (index === 0){
        index++
        return "s"+index
      }
    }
  }
}
</script>

<style scoped>
.slidershow{
  width: 100%;
  height: 100%;
  overflow: hidden;
  position: relative;
}
.navigation{
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
}
.bar{
  width: 50px;
  height: 10px;
  border: 2px solid #fff;
  margin: 6px;
  cursor: pointer;
  transition: 0.4s;
}
.bar:hover{
  background: #fff;
}

input[name="r"]{
    position: absolute;
    visibility: hidden;
}

.slides{
  width: 600%;
  height: 100%;
  display: flex;
}

.slide{
  width: 20%;
  transition: 1s;
}
.slide img{
  width: 100%;
  height: 100%;
}

/* 指定某一幅图平移，那么另外其他图也会跟着平移 */
#r0:checked ~ .s1{
  margin-left: 0;
}
#r1:checked ~ .s1{
  margin-left: -20%;
}
#r2:checked ~ .s1{
  margin-left: -40%;
}
#r3:checked ~ .s1{
  margin-left: -60%;
}
#r4:checked ~ .s1{
  margin-left: -80%;
}

</style>