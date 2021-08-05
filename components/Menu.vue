<template>
  <van-tabbar v-model="active" @change="onChange">
  <van-tabbar-item icon="home-o">Tab1</van-tabbar-item>
  <van-tabbar-item icon="search">Tab2</van-tabbar-item>
  <van-tabbar-item icon="friends-o">Tab3</van-tabbar-item>
  <van-tabbar-item icon="setting-o">Tab4</van-tabbar-item>
</van-tabbar>
</template>
<script>
export default {
  data() {
    return {
      active: 0,
      icon: {
        active: 'https://img01.yzcdn.cn/vant/user-active.png',
        inactive: 'https://img01.yzcdn.cn/vant/user-inactive.png',
      },
    };
  },
};
</script>

<style>

</style>