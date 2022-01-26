<template>
  <div>
    {{ pets }}
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    pets: null,
  }),
  mounted() {
    axios
      .get("https://petstore.swagger.io/v2/pet/findByStatus?status=available")
      .then((response) => (this.pets = response.data))
      .catch((error) => console.log(error));
  },
  // methods: {
  //   getPets() {
  //     let _this = this;
  //     axios
  //       .get("https://petstore.swagger.io/v2/pet/findByStatus?status=available")
  //       .then(function (response) {
  //         _this.pets = response.data;
  //         // _this.pets.forEach((pet) => {
  //         //   _this.pets.push(pet);
  //         // });
  //         console.log(response.data);
  //         // _this.pets.push(response.data[0]);
  //       });
  //   },
  // },
};
</script>