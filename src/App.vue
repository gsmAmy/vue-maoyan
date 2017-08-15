<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  created(){
	//设备独立像素
	var screenWidth = window.screen.width;
	//缩放因子
	var pixelRatio = window.devicePixelRatio;
	//物理分辨率
	var clientWidth = screenWidth * pixelRatio;
	//设置html字体大小
	document.getElementsByTagName("html")[0].style.fontSize = clientWidth / 10 + 'px';
	//动态设置meta
	var meta = document.createElement("meta");
	meta.name = 'viewport';
	meta.content = 'initial-scale='+1/pixelRatio+', maximum-scale='+1/pixelRatio+', minimum-scale='+1/pixelRatio+', user-scalable=no';
	document.getElementsByTagName("head")[0].appendChild(meta);
	
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
  margin-top: 60px;
}

</style>
