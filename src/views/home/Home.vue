<!--  -->
<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control
      class="tab-control"
      :titles="['流行', '新款', '精选']"
    ></tab-control>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
    <div>列表1</div>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar.vue";
import { getHomeMultidata, getHomeGoods } from "network/home";
import HomeSwiper from "./childComps/HomeSwiper.vue";
import RecommendView from "./childComps/RecommendView.vue";
import FeatureView from "./childComps/FeatureView.vue";
import TabControl from "../../components/content/tabControl/TabControl.vue";

export default {
  components: { NavBar, HomeSwiper, RecommendView, FeatureView, TabControl },
  name: "Home",
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        'pop': { page: 0, list: [] },
        'news': { page: 0, list: [] },
        'sell': { page: 0, list: [] },
      },
    };
  },
  //生命周期 - 创建完成（访问当前this实例）
  created() {
    this.getHomeData();
    this.getHomeGoodsData('pop',1);
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

    //获取商品数据
    getHomeGoodsData(type,page){
      getHomeGoods(type,page).then(res => {
        console.log(res)
      })
    }
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

.tab-control {
  position: sticky;
  top: 44px;
}
</style>
