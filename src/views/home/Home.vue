<template>
<div id="home">
  <nav-bar class="nav-bar"><div slot="center">购物街</div></nav-bar>
  <home-swiper :banners="banners"/>
  <recommend-view :recommends="recommend"/>
</div>

</template>
<script>
  import NavBar from "components/common/navbar/NavBar";
  import HomeSwiper from "./childrencomps/HomeSwiper";
  import RecommendView from "./childrencomps/RecommendView";
  import{getHomeMultidata} from "../../network/home";


  export default {
  name: "Home",
    data(){
    return{
      banners:[],
      recommend:[]

    }
    },
  components: {
    NavBar,
    HomeSwiper,
    RecommendView
  },
    created() {
    //1.请求多个数据
      getHomeMultidata().then(res => {
        this.banners=res.data.banner.list;
        this.recommend=res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
.nav-bar{
  background-color: var(--color-tint);
  color: #fff;
}

</style>
