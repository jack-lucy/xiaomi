<template>
  <div class="video">
    <Title :title="title"></Title>
    <div>
      <video-box
        v-for="(item, index) in videoInfo"
        :key="index"
        :videoInfo="item"
        class="video-item"
      ></video-box>
    </div>
  </div>
</template>

<script>
import Title from "./common/Title";
import VideoBox from "./common/VideoBox";

export default {
  components: {
    Title,
    VideoBox,
  },
  name: "",
  data() {
    return {
      title: "视频",
      videoInfo: [
        {
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e74c4ff741bcdfc5b28a48a43e4edc6d.jpg",
          videoUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/812358b69886e576c66a01f1f00affe9.mp4",
          title: "2021年春季新品发布会第一场",
          desc: "",
        },
        {
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/101b19aca4bb489bcef0f503e44ec866.jpg",
          videoUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/11c70c96529b6e6938567ec1aa0910e0.mp4",
          title: "Redmi 10X系列发布会",
          desc: "Redmi 10X系列发布会",
        },
        {
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/96563e75833ba4563bd469dd28203b09.jpg",
          videoUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/7cdabcaa763392c86b944eaf4e68d6a3.mp4",
          title: "小米10 青春版 发布会",
          desc: "",
        },
        {
          imgUrl:
            "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/2fd26bb99b723337a2f8eaba84f7d5bb.jpg",
          videoUrl:
            "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/e25d81c4922fca5ebe51877717ef9b76.mp4",
          title: "小米10 8K手机拍大片",
          desc: "",
        },
      ],
    };
  },
  methods: {
    // initVideo() {
    //     //初始化视频方法
    //     let myPlayer = this.$video(myVideo, {
    //         //确定播放器是否具有用户可以与之交互的控件。没有控件，启动视频播放的唯一方法是使用autoplay属性或通过Player API。
    //         controls: true,
    //         //自动播放属性,muted:静音播放
    //         autoplay: "muted",
    //         //建议浏览器是否应在<video>加载元素后立即开始下载视频数据。
    //         preload: "auto",
    //         //设置视频播放器的显示宽度（以像素为单位）
    //         width: "800px",
    //         //设置视频播放器的显示高度（以像素为单位）
    //         height: "400px"
    //     });
    //     }
  },
};
</script>

<style scoped>
.video {
  height: 357px;
}
.video-item {
  float: left;
}
.video-item:nth-child(2) {
  margin-left: 14px;
}
.video-item:nth-child(3) {
  margin-left: 14px;
}
.video-item:nth-child(4) {
  margin-left: 14px;
}

#myVideo {
  height: 1000px;
  width: 1000px;
}
</style>