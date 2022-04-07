<template>
  <form @submit.prevent="submit">
    <v-text-field v-model="name" label="Name" required></v-text-field>

    <v-text-field v-model="message" label="Message" required></v-text-field>

    <v-btn class="mr-4" type="submit">submit </v-btn>
    <v-btn color="error" class="mr-4" @click="clear"> clear </v-btn>
  </form>
</template>
<script>
import axios from 'axios';
export default {
  components: {},
  data: () => ({
    name: "",
    message: "",
  }),
  methods: {
    submit(e) {
      axios({
        url: "https://formspree.io/f/xjvlrqgb",
        method: "post",
        headers: {
          Accept: "application/json",
        },
        data: {
          name: this.$data.name,
          message: this.$data.message,
        },
      });
    },
    clear() {
      this.name = "";
      this.message = "";
    },
  },
};
</script>
