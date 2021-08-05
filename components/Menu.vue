<template>
  <van-tabbar style="padding-top:5px;border-top-left-radius:10px;border-top-right-radius:10px" v-model="active" @change="onChange">
  <van-tabbar-item icon="wap-home-o">Home</van-tabbar-item>
  <van-tabbar-item icon="search">APP2</van-tabbar-item>
  <van-tabbar-item icon="friends-o">APP3</van-tabbar-item>
  <van-tabbar-item icon="setting-o">APP4</van-tabbar-item>
</van-tabbar>
</template>
<script>
export default {
  data() {
    return {
      active: 0,
    };
  },
};
</script>

<style>

</style>