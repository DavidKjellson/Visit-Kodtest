<template>
  <div class="frame">
    <Header />
    <!-- <div class="header">LLLLLL</div> -->
    <slot />
  </div>
</template>

<script>
import Header from "./Header.vue";
export default {
  components: {
    Header,
  },
};
</script>


<style scoped>
.frame {
  width: 420px;
  border: solid;
  border-width: 1px;
  border-radius: 0.5rem;
  justify-content: space-around;
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