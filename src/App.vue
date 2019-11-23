<template>
  <div id="app">
     <router-view></router-view>
  </div>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>
<style lang="less">
  html,body{
    height: 100% !important;
    margin: 0 auto;
  }
 #app{
   height: 100%;
   background-color: #315481;
   background-image: linear-gradient(180deg,#315481,#918e82);
 }
 .clearfloat:after{display:block;clear:both;content:"";visibility:hidden;height:0}
</style>
