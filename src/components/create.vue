<template>
  <v-container>
    <h1>NUEVO POST</h1>

    <v-text-field v-model="title" label="TITULO" required></v-text-field>
    <v-text-field v-model="body" label="CUERPO" required></v-text-field>
    <v-btn depressed color="#2196F3" v-on:click="guardar"> GUARDAR </v-btn>

  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      title: "",
      body: "",
    };
  },
  methods: {
      async guardar() {
        const { data: response } = await axios.post("https://jsonplaceholder.typicode.com/posts", 
        {
            title: this.title,
            body: this.body
        });

        console.log(response);
      }
  }
};
</script>

<style>
</style>