<template>
  <div>
    <Header></Header>
    <!-- 路由子组件出口的地方 -->
    <router-view></router-view>
    <!-- 在Home、Search显示，在登录和注册隐藏 -->
    <Footer v-show="$route.meta.show"></Footer>
  </div>
</template>

<script>
//引入
import Header from './components/Header'
import Footer from './components/Footer'
export default {
  name: 'App',
  components:{
    Header,Footer
  }
  
}
</script>

<style scoped>

</style>
