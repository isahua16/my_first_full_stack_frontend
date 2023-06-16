<template>
  <div>
    <button v-if="error === true">Retry</button>
    <p v-if="candies.length === 0">No Candies To Display</p>
    <article v-for="(candy, i) in candies" :key="i">
      <h3>{{ candy["name"] }}</h3>
      <p>{{ candy[`description`] }}</p>
      <img :src="candy[`image_url`]" :alt="`Image of ${candy['name']}`" />
      <delete-candy :candy_id="candy[`id`]"></delete-candy>
    </article>
  </div>
</template>

<script>
import axios from "axios";
import DeleteCandy from "@/components/DeleteCandy.vue";
export default {
  components: {
    DeleteCandy,
  },
  data() {
    return {
      candies: [],
      error: false,
    };
  },
  methods: {
    get_candy() {
      axios
        .request({
          url: `${process.env.VUE_APP_BASE_DOMAIN}/api/candy`,
        })
        .then((res) => {
          res;
          this.error = false;
          this.candies = res[`data`];
        })
        .catch((err) => {
          err;
          this.error = true;
        });
    },
  },
  mounted() {
    this.get_candy();
    this.$root.$on(`reload_candy`, this.get_candy);
  },
};
</script>

<style scoped>
</style>