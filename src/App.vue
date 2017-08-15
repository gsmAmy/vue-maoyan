<template>
  <div id="app">
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
	// document.getElementsByTagName("html")[0].style.fontSize = clientWidth / 10 + 'px';
  	document.documentElement.style.fontSize = clientWidth / 10 + 'px';
	//动态设置meta
	var meta = document.createElement("meta");
	meta.name = 'viewport';
	meta.content = 'initial-scale='+1/pixelRatio+', maximum-scale='+1/pixelRatio+', minimum-scale='+1/pixelRatio+', user-scalable=no';
	document.getElementsByTagName("head")[0].appendChild(meta);
	//设置dpr
	var dpr = 1;
	if(pixelRatio >=2 && pixelRatio <3){
		dpr = 2
	}else if(pixelRatio>=3){
		dpr = 3;
	}
	document.documentElement.dataset.dpr = dpr;
  }
}
</script>

<style lang="less">
@import "./assets/less/common.less";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
