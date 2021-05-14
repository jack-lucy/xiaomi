<template>
  <div class="time-box">
    <div class="round">14:00 场</div>
    <img src="../../assets/img/ms.png" alt="" />
    <div class="desc">距离结束还有</div>
    <div class="countdown clearfix">
      <span id="h"></span>
      <i>:</i>
      <span id="m"></span>
      <i>:</i>
      <span id="s"></span>
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
  mounted() {
    // 如果想让时间能够显示，那么设置的时间必须要大于今日的日期
    var endTime = new Date("2021-05-11 14:00:00");
    //把年月日时分秒的时间转换成为毫秒数
    var endSeconds = endTime.getTime(); //结束时间的毫秒数
    //定义变量  天数 小时 分钟  秒数
    var h = 0;
    var m = 0;
    var s = 0;

    //设置定时器  实现一个秒杀效果
    var timer = setInterval(qiang, 1000);

    function qiang() {
      // 获取当前系统时间
      var nowTime = new Date();
      // 获取当前时间差---nowTime.getTime()现在时间的毫秒数
      var remain = parseInt((endSeconds - nowTime.getTime()) / 1000);
      //判断秒杀是否过期
      if (remain > 0) {
        //1.计算剩余天数  （除以60*60*24  取整数  获取剩余天数）
        // d = parseInt(remain/86400)
        //2.计算剩余小时（除以60*60 转换成为小时了  与24进行取模   获取剩余小时）
        h = parseInt((remain / 3600) % 24);
        //3.计算剩余分钟（除以60  转换成为分钟了  与60进行取模   获取剩余分钟）
        m = parseInt((remain / 60) % 60);
        //4.计算剩余秒数（与60进行取模   获取剩余秒数）
        s = parseInt(remain % 60);

        //统一利用两位数 表示 剩余的天、小时、分钟、秒
        // d= d < 10 ? '0' + d:d;
        h = h < 10 ? "0" + h : h;
        m = m < 10 ? "0" + m : m;
        s = s < 10 ? "0" + s : s;
      } else {
        // 秒杀过期  取消定时器
        clearInterval(timer);
        h = m = s = "0";
      }
      //将剩余的天数、小时、分钟、秒  小时到指定网页中去
      // document.getElementById("d").innerHTML = d + '天';
      document.getElementById("h").innerHTML = h;
      document.getElementById("m").innerHTML = m;
      document.getElementById("s").innerHTML = s;
    }
  },
};
</script>

<style scoped>
.time-box {
  float: left;
  width: 234px;
  height: 340px;
  margin: left 14px;
  padding-top: 39px;
  border-top: 1px solid red;
  background: #f1eded;
  text-align: center;
}
.round {
  font-size: 21px;
  color: #ef3a3b;
  width: 234px;
  height: 31.2px;
  padding-top: 15px;
}
.time-box img {
  margin: 25px 0;
  width: 34px;
  height: 53px;
}
.desc {
  color: rgba(0, 0, 0, 0.54);
  font-size: 15px;
}
.countdown {
  height: 300px;
  width: 168px;
  margin: 28px auto 0;
}
.countdown span {
  width: 46px;
  height: 46px;
  background: #605751;
  color: #fff;
  font-size: 24px;
  line-height: 46px;
  float: left;
}
.countdown i {
  width: 15px;
  float: left;
  height: 46px;
  line-height: 46px;
  color: #605751;
  font-size: 28px;
  font-style: normal;
}
</style>