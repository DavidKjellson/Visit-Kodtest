<template>
  <div class="frame">
    <table>
      <Header />
      <slot name="table" />
    </table>
    <Footer>
      <slot name="footer" />
    </Footer>
  </div>
</template>

<script>
import Footer from "./Footer.vue";
import Header from "./Header.vue";

export default {
  components: {
    Footer,
    Header,
  },
  data: () => ({
    statuses: ["All", "Available", "Pending", "Sold"],
  }),
};
</script>


<style scoped>
.frame {
  width: 75%;
  border: solid;
  border-width: 1px;
  border-radius: 0.5rem;
  border-color: #4f4789;
  justify-content: space-around;
  font-size: 1.2rem;
  width: 100%;
  /* border-radius: 0.1rem 0.1rem 0 0; */
}
table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
}
</style>