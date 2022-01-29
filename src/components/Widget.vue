<template>
  <div class="widget">
    <!-- <div class="filter">
      <label
        ><input type="radio" v-model="filteredPets" value="All" /> All</label
      >
      <label
        ><input type="radio" v-model="filteredPets" value="Available" />
        Available</label
      >
      <label
        ><input type="radio" v-model="filteredPets" value="Pending" />
        Pending</label
      >
      <label
        ><input type="radio" v-model="filteredPets" value="Sold" /> Sold</label
      >
    </div> -->
    <Frame
      ><table>
        <Header />
        <tr v-for="(pet, idx) in filteredPets.slice(0, 5)" :key="idx">
          <th>{{ pet.name }}</th>
          <th>{{ pet.id }}</th>
          <th v-if="pet.tags[0] != undefined">
            {{ pet.tags[0].id }}, {{ pet.tags[0].name }}
          </th>
        </tr>
      </table></Frame
    >
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
    all: "All",
    api: "https://petstore.swagger.io/v2/pet/findByStatus?status=available,pending,sold",
    pets: null,
    statuses: ["Available", "Pending", "Sold"],
  }),
  computed: {
    filteredPets: {
      get: function () {
        let status = this.all;
        if (status === "All") {
          return this.pets;
        } else {
          return this.pets.filter(function (pet) {
            return pet.status === status;
          });
        }
      },
      set: function (newValue) {
        this.$store.state.pets = newValue;
      },
    },
  },
  mounted() {
    axios
      .get(this.api)
      .then((response) => (this.pets = response.data))
      .catch((error) => console.log(error));
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
  border-collapse: collapse;
}
</style>