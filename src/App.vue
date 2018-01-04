<template>
  <div id="app">
    <img src="../static/orient_tips.png" class='orention' v-if='show_orention'>
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'app',
  mounted:function(){
    //移动端的浏览器一般都支持window.orientation这个参数，通过这个参数可以判断出手机是处在横屏还是竖屏状态。
    window.addEventListener("onorientationchange" in window ? "orientationchange" : "resize", function() {
      if (window.orientation === 180 || window.orientation === 0) {
        this.show_orention = true;
      }
      if (window.orientation === 90 || window.orientation === -90 ){
          this.show_orention = false;
      }
    }, false);
  },
  data(){
    return{
      show_orention:false
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
html,body{
  width: 100%;
  height: 100%;
  background-color: #222;
  margin: 0;
}
.orention{
  width: 100%;
  height: 100%;
  z-index: 99;
}
</style>
