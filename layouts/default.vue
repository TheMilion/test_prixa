<template>
  <client-only>
    <div>
      <div class="app-page" style="overflow-y: scroll">
          <Nuxt />
      </div>
      <Menu />
    </div>
  </client-only>
</template>

<script>
import Menu from '~/components/Menu.vue';
export default {
  components: { Menu },};
</script>

<style scoped>
.app-page {
  height: 88.2%;
}
</style>
