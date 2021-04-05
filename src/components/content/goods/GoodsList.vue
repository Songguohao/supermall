<!-- Goods -->
<template>
  <div class="goods">
    <goods-list-item
      v-for="(item, index) in goods"
      :goodsItem="item"
      :key="index"
    ></goods-list-item>
  </div>
</template>

<script>
import GoodsListItem from "./GoodsListItem.vue";
export default {
  components: { GoodsListItem },
  name: "GoodsList",
  props: {
    goods: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {};
  },
  //生命周期 - 创建完成（访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（访问DOM元素）
  mounted() {},
};
</script>
<style scoped>
/* @import url(); 引入css类 */
.goods {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;

  padding: 2px;
}


</style>
