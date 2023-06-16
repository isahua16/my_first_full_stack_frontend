<template>
  <div>
    <button @click="delete_candy">DELETE</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: {
    candy_id: Number,
  },
  methods: {
    delete_candy() {
      axios
        .request({
          url: `${process.env.VUE_APP_BASE_DOMAIN}/api/candy`,
          method: `DELETE`,
          data: {
            id: this.candy_id,
          },
        })
        .then((res) => {
          console.log(res);
        })
        .catch((err) => {
          err;
        });
    },
  },
};
</script>

<style scoped>
</style>