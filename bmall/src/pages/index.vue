<template>
  <div>
      <router-view></router-view>
      <van-tabbar v-model="active" active-color="orange">
  <van-tabbar-item icon="home-o">首页</van-tabbar-item>
  <van-tabbar-item icon="apps-o">分类</van-tabbar-item>
  <van-tabbar-item icon="shopping-cart-o">购物车</van-tabbar-item>
  <van-tabbar-item icon="contact">我的</van-tabbar-item>
</van-tabbar>
  </div>
</template>

<script>
export default {
data(){
    return{
        active:0
    }
}
}
</script>

<style>

</style>