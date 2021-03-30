<!--  -->
<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物车</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar.vue";
import { getHomeMultidata } from "network/home";
import HomeSwiper from "./childComps/HomeSwiper.vue";
import RecommendView from './childComps/RecommendView.vue';
import FeatureView from './childComps/FeatureView.vue';

export default {
  components: { NavBar, HomeSwiper, RecommendView, FeatureView },
  name: "Home",
  data() {
    return {
      banners: [],
      recommends: [],
    };
  },
  //生命周期 - 创建完成（访问当前this实例）
  created() {
    this.getHomeData();
  },
  //生命周期 - 挂载完成（访问DOM元素）
  mounted() {},
  methods: {
    getHomeData() {
      getHomeMultidata().then((res) => {
        this.banners = res.data.data.banner.list;
        this.recommends = res.data.data.recommend.list;
      });
    },
  },
};
</script>
<style scoped>
/* @import url(); 引入css类 */
@import "../../assets/css/basecss.css";
#home {
  padding-top: 44px;
}
.home-nav {
  background-color: var(--color-tint);
  color: #fff;

  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
</style>
