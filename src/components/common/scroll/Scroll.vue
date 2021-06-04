<template>
<!--  ref如果是绑定在组件中的，则通过‘this.$refs.refname’获取到的是一个组件对象-->
  <!--  ref如果是绑定在普通的元素中的，则通过‘this.$refs.refname’获取到的是一个元素对象-->
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  import BScroll from "better-scroll"

    export default {
        name: "Scroll",
      props: {
        probeType: {
          type: Number,
          default: 0
        },
        pullUpLoad: {
          type: Boolean,
          default: false
        }
      },
      data() {
          return {
            scroll: null
          }
      },
      mounted() {
          // 如果在多个元素标签中（也可以是不同组件中的）用了相同的class，document.querySelector()拿到的元素标签不确定
          this.scroll = new BScroll(this.$refs.wrapper, {
            click: true,
            probeType: this.probeType,
            pullUpLoad: this.pullUpLoad
          })

        this.scroll.on('scroll', (position) => {
          this.$emit('scroll', position)
        })

        this.scroll.on('pullingUp',() => {
          this.$emit('pullingUp')
        })
      },
      methods: {
          scrollTo(x, y, time=300) {
            this.scroll.scrollTo(x, y, time)
          },
        finishPullUp() {
            this.scroll.finishPullUp()
        }
      }
    }
</script>

<style scoped>

</style>
