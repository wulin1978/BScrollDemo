<template>
  <div id="app">
    <div class='title'>better-scroll 使用例子</div>
    1、<router-link to='/demo1' class='demo' tag='div'><a>最简单的滚动例子</a></router-link>
    <div class='demo'>2、下拉刷新例子</div>
    <div class='demo'>3、上拉加载例子</div>
    <div class='demo'>demo</div>
    <div class='demo'>demo</div>
    <router-view/>
  </div>
</template>

<script>
export default {
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  position: absolute;
  bottom: 0px;
  top: 0px;
  margin-top:50px;
  width:100%;
  text-align: center;
}
.title {
  font-size: 30px;
  font-weight: 150px;
  margin-bottom:50px;
}
.demo{
  margin:25px 6px;
  display: inline-block;
  width: 160px;
  text-align: left;
}
ul,li{
    list-style: none;
    margin: 0px;
    padding: 10px;
}
</style>
