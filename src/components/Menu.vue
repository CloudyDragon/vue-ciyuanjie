<template>
  <div id="nav">
    <div class="menu-button" @click="test">
      <canvas id="mycanvas" width="50px" height="49px" style="background-color:white;"></canvas>
    </div>
    <transition enter-active-class="animated fadeIn"
                leave-active-class="animated fadeOut">
      <MenuChild :num="count" v-show="menuShow"/>
    </transition>
  </div>
</template>

<script>
import animate from 'animate.css'
import MenuChild from './MenuChild.vue'

export default {
  name: 'Menu',
  props: ['count'],
  data () {
    return {
      menuShow: true
    }
  },
  methods: {
    test () {
      this.menuShow = !this.menuShow
      var c = document.getElementById('mycanvas')
      var ctx = c.getContext('2d')
      ctx.fillStyle = 'black'
      ctx.fillRect(0, 0, 50, 50)
      ctx.fillStyle = '#fff'
      ctx.fillRect(10, 7, 30, 6)
      ctx.fillRect(10, 20, 30, 6)
      ctx.fillRect(10, 35, 30, 6)
    }
  },
  mounted: function() {
    //用于绘制菜单button的Canvas
    this.$nextTick(function() {
      var c = document.getElementById('mycanvas')
      var ctx = c.getContext('2d')
      ctx.fillStyle = '#000'
      ctx.fillRect(0, 0, 50, 50)
      ctx.fillStyle = '#fff'
      ctx.fillRect(10, 7, 30, 6)
      ctx.fillRect(10, 20, 30, 6)
      ctx.fillRect(10, 35, 30, 6)
    })
  },
  components: {
    MenuChild
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
#nav
  display: flex;
  flex-direction: row-reverse
  width: 100%;
  height: 50px;
  border-bottom: 1px solid rgba(255, 0, 0, .3);
  .menu-button
    display: block;
    height: 50px;
    width: 50px;
    box-sizing:border-box;
    cursor: pointer;
    span
      display: inline-block;
      height: 50px;
      line-height: 50px;
    #mycanvas
      display: block;
      border-radius: 0%;

</style>
