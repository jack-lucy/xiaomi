<template>
  <!-- 视频播放区域  这里一定要使用v-if-->
  <div class="main" v-if="videoInfo.playStatus">
    <div class="play-video">
      <div class="title">
        <p>{{ videoInfo.title }}</p>
        <a href="javascript:void(0);" @click="closeVideo()">
          <span class="iconfont icon-baseline-close-px"></span>
        </a>
      </div>
      <video
        id="myVideo"
        class="video-js vjs-big-play-centered vjs-fluid"
        controls
        preload="auto"
        :poster="videoInfo.imgUrl"
      >
        <source
          type="video/mp4"
          src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/812358b69886e576c66a01f1f00affe9.mp4"
        />
      </video>
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
  methods: {
    closeVideo() {
      //这里的playStatus不是父组件数据，而是子组件的数据
      this.videoInfo.playStatus = false;
      // console.log(this.videoInfo);
    },
  },
  props: ["videoInfo"],
};
</script>

<style scoped>
/* 视频播放区域 */
.main {
  position: fixed;
  width: 100%;
  height: 1000px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: rgba(0, 0, 0, 0.3);
  z-index: 990;
}
.play-video {
  position: fixed;
  width: 880px;
  height: 555px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -60%);
}
.play-video .title {
  position: relative;
  height: 60px;

  background-color: #f5f5f5;
}
.title p {
  float: left;
  margin-left: 20px;
  font-size: 18px;
  font-weight: 400;
  color: #424242;
  line-height: 60px;
  vertical-align: middle;
}
.title a {
  /* 浮动元素想要垂直居中，目前只想到使用增加margin方案 */
  float: right;
  margin-top: 15px;
  width: 30px;
  height: 30px;
  line-height: 45px;
  margin-right: 20px;
}
.title a:hover {
  border-radius: 20px;
  background: red;
}
.title a span:hover {
  color: #fff;
}
.title span {
  width: 24px;
  height: 24px;
  font-size: 24px;
  font-weight: 400;
  color: #424242;
  line-height: 30px;
}
#myVideo {
  width: 880px;
  height: 555px;
}
</style>