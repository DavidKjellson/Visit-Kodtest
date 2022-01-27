<template>
  <div class="frame">
    <!--     <table>
      <tr>
        <Header
          ><th>Company</th>
          <th>Contact</th>
          <th>Country</th></Header
        >
      </tr>
      <tr>
        <td>k</td>
        <td>k</td>
        <td>k</td>
      </tr>
    </table> -->
    <!-- <Header>????</Header> -->
    <slot />
  </div>
</template>

<script>
// import Header from "./Header.vue";
// export default {
//   components: {
//     Header,
//   },
// };
</script>


<style scoped>
.frame {
  width: 500px;
  border: solid;
  border-width: 1px;
  border-radius: 0.5rem;
  justify-content: space-around;
  font-size: 1.2rem;
}
/* .header {
  display: block;
  text-align: center;
  color: #fff;
  background-color: #6184a8;
  padding: 2%;
  border-top-right-radius: 4px;
  border-top-left-radius: 4px;
} */
</style>