<template>
  <div>
    <Header></Header>
    <router-view></router-view>
    <!-- 在login、register模块隐藏 -->
    <!-- v-show="$route.path == '/home' || $route.path == '/search'" -->
    <!-- v-show="$route.path !== '/login' && $route.path !== '/register'" -->
    <Footer
      v-show="$route.path !== '/login' && $route.path !== '/register'"
    ></Footer>
  </div>
</template>

<script>
import Header from "./components/Header/index.vue";
import Footer from "./components/Footer/index.vue";
export default {
  name: "",
  components: {
    Header,
    Footer,
  },
  mounted() {
    // 通知vuex发请求，获取数据，存储到仓库中
    // 派发一个action 获取商品分类的三级列表的数据
    this.$store.dispatch("home/categoryList");
  },
};
</script>

<style lang='less' scoped>
</style>
