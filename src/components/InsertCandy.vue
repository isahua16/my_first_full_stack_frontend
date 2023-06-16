<template>
  <div>
    <input type="text" placeholder="Name" ref="name_input" />
    <input type="text" placeholder="Image URL" ref="image_url_input" />
    <input type="text" placeholder="Description" ref="description_input" />
    <button @click="submit_candy">Submit</button>
    <h3>{{ message }}</h3>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      message: undefined,
    };
  },
  methods: {
    submit_candy() {
      this.message = "loading";
      axios
        .request({
          url: `${process.env.VUE_APP_BASE_DOMAIN}/api/candy`,
          method: "POST",
          data: {
            name: this.$refs["name_input"].value,
            image_url: this.$refs["image_url_input"].value,
            description: this.$refs["description_input"].value,
          },
        })
        .then((res) => {
          res;
          this.message = "Candy Upload Succesful";
        })
        .catch((err) => {
          err;
          this.message = "Candy Upload Failed";
        });
    },
  },
};
</script>

<style scoped>
</style>