<template>
  <swiper>
    <swiper-item v-for="item in banners">
      <!--        用的是变量中的某个属性，需要动态绑定-->
      <a :href="item.link">
        <img :src="item.image" alt="">
      </a>
    </swiper-item>
  </swiper>
</template>

<script>
  import {Swiper, SwiperItem} from "components/common/swiper"

  export default {
        name: "HomeSwiper",
    props: {
      banners: {
        type: Array,
        default() {
          return []
        }
      }
    },
    components: {
          Swiper,
          SwiperItem
    }
    }
</script>

<style scoped>

</style>
