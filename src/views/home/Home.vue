<!--  -->
<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物车</div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar.vue";
import { getHomeMultidata } from "network/home";
export default {
  components: { NavBar },
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
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
</style>
