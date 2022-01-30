<template>
  <tr class="header">
    <th v-for="category in categories" :key="category">{{ category }}</th>
  </tr>
</template>

<script>
export default {
  data: () => ({
    categories: ["Name", "ID", "Tags"],
  }),
};
</script>

<style scoped>
.header {
  color: #ffffff;
  height: auto;
  background-color: #4f4789;
  width: 100%;
  margin: 0 auto;
  /* #261447 */
}
</style>