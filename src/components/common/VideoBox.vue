<template>
  <div class="video-item">
    <a
      href="javascript:void(0);"
      @click="playVideo(videoInfo.videoUrl, videoInfo.imgUrl, videoInfo.title)"
    >
      <div
        class="figure-img"
        ref="figure-img"
        @mouseenter="colorChange"
        @mouseleave="colorBack"
      >
        <img :src="videoInfo.imgUrl" alt="" />
        <span ref="iconfont">
          <i class="iconfont icon-bofang"></i>
        </span>
      </div>
      <h3 class="title">{{ videoInfo.title }}</h3>
      <p class="desc">{{ videoInfo.desc }}</p>
    </a>
    <video-player :videoInfo="urls"></video-player>
  </div>
</template>

<script>
import VideoPlayer from "./VideoPlayer";
export default {
  components: {
    VideoPlayer,
  },
  name: "",
  data() {
    return {
      // playStatus: false,
      urls: { videoUrl: "", imgUrl: "", title: "", playStatus: false },
    };
  },
  props: ["videoInfo"],
  methods: {
    colorChange() {
      var icon = this.$refs.iconfont;
      icon.style = "background: #ff6700;";
    },
    colorBack() {
      var icon = this.$refs.iconfont;
      icon.style = "background: transparent";
    },
    // 播放视频
    playVideo(videoUrl, imgUrl, title) {
      this.urls.playStatus = true;
      this.urls.videoUrl = videoUrl;
      this.urls.imgUrl = imgUrl;
      this.urls.title = title;
      console.log(this.urls.playStatus);
    },
  },
};
</script>

<style scoped>
.video-item {
  width: 296px;
  height: 285px;
  /* margin-left: 7px; */
  margin-bottom: 14px;
  text-align: center;
  background: #fff;
  transition: all 0.3s;
}
/* .video-item:hover{
  transform: translateY(-1px);
  box-shadow: 5px 5px 20px #ccc;
} */
/* 1.图片区域 */
.figure-img {
  position: relative;
  width: 296px;
  height: 180px;
  margin: 0 0 28px;
}
img {
  width: 296px;
  height: 180px;
}
.figure-img span {
  position: absolute;
  left: 20px;
  bottom: 10px;
  width: 32px;
  height: 20px;
  line-height: 16px;
  border: 2px solid #fff;
  border-radius: 12px;
  background-color: rgba(0, 0, 0, 0.6);
  color: #fff;
}
/* .figure-img:hover{
  background: #ff6700;
} */
.figure-img i {
  position: relative;
  text-align: center;
  font-size: 10px;
}

.title {
  margin: 0 14px 6px;
  font-size: 14px;
  font-weight: 400;
  text-align: center;
  color: #333;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
.desc {
  height: 18px;
  margin: 0 14px;
  font-size: 12px;
  color: #b0b0b0;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
</style>