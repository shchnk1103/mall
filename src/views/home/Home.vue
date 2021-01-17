<template>
  <div id="home">
    <nav-bar class="home-navbar">
      <template #center>
        首页
      </template>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
import {getHomeMultiData} from "@/network/home";

export default {
  name: "Home",
  components: {
    NavBar,
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    getHomeMultiData().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    })
  },
}
</script>

<style scoped>
.home-navbar {
  background-color: var(--color-tint);
  color: #fff;
}
</style>
