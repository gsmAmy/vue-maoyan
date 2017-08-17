<template>
<div class="main-warp">
	<header class="home">
		<a class="city">苏州</a>
		<div class="title">猫眼电影</div>
	</header>
	<div class="content">
		<ul class="tab-menu" >
			<li v-for="(item,index) in tabmenu" v-bind:key="index" :class="{active:activeState==index}" @click="tabClick(index)">{{item}}</li>
		</ul>
		<div class="line"></div>
		<ul class="movie-list">
			<li class="list-item">
				<div class="movie-img">
					<img src="http://p0.meituan.net/movie/4ddfd25f99b14400c6bbbca62beffa10214626.jpg.webp@128w_180h">
				</div>
				<div class="introduce">
					<p class="move-tit">杀破狼·贪狼</p>
					<p>剧情,动作,犯罪</p>
					<p>主演:古天乐,吴樾,林家栋</p>
					<p class="beizhu">今天123家影院放映1348场</p>
				</div>
				<div class="right">
					<p class="goal">8.4分</p>
					<span>购票</span>
				</div>
			</li>
		</ul>
	</div>
</div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
	  activeState:0,
	  tabmenu:["影片","影院"],
	  url:'/?_lxsdk_rnd=15deef8cc0b'
    }
  },
  created(){
	  this.$Axios
		  .post(this.url)
		  .then(res=>{res.data;console.log(res)})
		  
  },
  methods:{
	  tabClick(index){
		  this.activeState = index;
	  }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
@import "../assets/less/hello.less";
</style>
