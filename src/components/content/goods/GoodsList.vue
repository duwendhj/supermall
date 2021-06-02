<template>
  <div class="goods-list">
    <goods-list-item v-for="item in goods" :goods-item="item" class="item"/>
  </div>
</template>

<script>
  import GoodsListItem from "./GoodsListItem";

    export default {
      name: "GoodsList",
      components: {
        GoodsListItem
      },

      props: {
        goods: {
          type: Array,
          default() {
            return []
          }
        }

      }
    }
</script>

<style scoped>
.goods-list {
  display: flex;
  /*不设置wrap flex布局会把所有盒子放在一行*/
  flex-wrap: wrap;
  padding: 5px;
  /*均等分*/
  justify-content: space-around;
}

.goods-list .item {
  width: 48%;
}

</style>
