<template>
  <div class="widget">
    <Frame>
      <Header>
        <table>
          <tr>
            <th>Name</th>
            <th>ID</th>
            <th>Tags</th>
          </tr>
        </table></Header
      >
      <table>
        <tr>
          <th>Hund</th>
          <th>Hund</th>
          <th>Hund</th>
        </tr>
      </table></Frame
    >
    <!-- <button>Available</button>
    <button>Pending</button>
    <button>Sold</button>
    <div v-for="(pet, idx) in pets" :key="idx">
      {{ pet.name }} - {{ pet.id }} -
      <span v-if="pet.tags[0] != undefined"
        >{{ pet.tags[0].id }} - {{ pet.tags[0].name }}</span
      >
      -
      {{ pet.status }}
    </div> -->
  </div>
</template>

<script>
import axios from "axios";
import Frame from "./Frame.vue";
import Header from "./Header.vue";

export default {
  components: {
    Frame,
    Header,
  },
  data: () => ({
    api: "https://petstore.swagger.io/v2/pet/findByStatus?status=available,pending,sold",
    pets: null,
    // available: "available",
    // pending: "pending",
  }),
  // methods: {
  //   setAvailable() {
  //     this.status = "available";
  //     console.log(this.api + this.status);
  //   },
  //   setPending() {
  //     this.status = "pending";
  //     console.log(this.api + this.status);
  //   },
  // },
  mounted() {
    // let available = this.api + this.available;
    axios
      .get(this.api)
      .then((response) => (this.pets = response.data))
      .catch((error) => console.log(error));
    // console.log(this.api);
  },
};
</script>

<style scoped>
.widget {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  /* width: 100vw; */
  height: 50vh;
}
table {
  table-layout: fixed;
  width: 100%;
}
</style>