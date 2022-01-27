<template>
  <div class="widget">
    <Frame
      ><table>
        <Header />

        <tr v-for="(pet, idx) in pets.slice(0, 5)" :key="idx">
          <th>{{ pet.name }}</th>
          <th>{{ pet.id }}</th>
          <th v-if="pet.tags[0] != undefined">
            {{ pet.tags[0].id }}, {{ pet.tags[0].name }}
          </th>
        </tr>
      </table></Frame
    >

    <!-- <div v-for="(pet, idx) in pets.slice(0, 5)" :key="idx">
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
  table-layout: auto;
  width: 100%;
  border-collapse: collapse;
}
</style>