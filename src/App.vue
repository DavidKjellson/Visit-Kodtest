<template>
  <div id="app">
    <div class="widget">
      <Frame>
        <template v-slot:table>
          <tr v-for="(pet, idx) in filteredPets.slice(0, 5)" :key="idx">
            <th>{{ pet.name }}</th>
            <th>{{ pet.id }}</th>
            <th v-if="pet.tags[0] != undefined">
              {{ pet.tags[0].id }}, {{ pet.tags[0].name }}
            </th>
          </tr>
        </template>
        <template v-slot:footer id="pets">
          <label
            v-for="status in statuses"
            :key="status"
            :class="{ checked: all === status.toLowerCase() }"
            ><input
              type="radio"
              :value="status.toLowerCase()"
              v-model="all"
            />{{ status }}</label
          >
        </template>
      </Frame>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Frame from "./components/Frame.vue";

export default {
  components: {
    Frame,
  },
  data: () => ({
    all: "all",
    api: "https://petstore.swagger.io/v2/pet/findByStatus?status=available,pending,sold",
    pets: [],
    statuses: ["All", "Available", "Pending", "Sold"],
  }),
  computed: {
    filteredPets: function () {
      let status = this.all;
      if (status === "all") {
        return this.pets;
      } else {
        return this.pets.filter(function (pet) {
          return pet.status === status;
        });
      }
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


<style>
body {
  background-color: #f7f7ff;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.widget {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: top;
  /* width: 100vw; */
  height: 50vh;
}
table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
}
</style>
