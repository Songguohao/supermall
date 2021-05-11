<!--  -->
<template>
  <div id="detail">
    <detail-nav-bar></detail-nav-bar>
    <detail-swiper :topImages="topImages"></detail-swiper>
  </div>
</template>

<script>
import DetailNavBar from "./childComps/DetailNavBar.vue";
import { getDetail } from "network/detail";
import DetailSwiper from './childComps/DetailSwiper.vue';
export default {
  components: { DetailNavBar, DetailSwiper },
  name: "Detail",
  data() {
    return {
      iid: null,
      topImages: [],
    };
  },
  //生命周期 - 创建完成（访问当前this实例）
  created() {
    this.iid = this.$route.params.iid;
    getDetail(this.iid).then((res) => {
      this.topImages = res.data.result.itemInfo.topImages;
    });
  },
  //生命周期 - 挂载完成（访问DOM元素）
  mounted() {},
};
</script>
<style scoped>
/* @import url(); 引入css类 */
</style>
