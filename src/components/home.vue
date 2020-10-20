<template>
  <v-container>
    <h1>POSTS</h1>
    <br />

    <v-row v-for="post in posts" v-bind:key="post">
      <v-col cols="12" md="6">
        <post :post="post"></post>
      </v-col>
    </v-row>

  </v-container>
</template>

<script>
import axios from 'axios';
import post from './post';

export default {
  data() {
    return {
      posts: []
    };
  },
  created: async function() {
        let {data: response} = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10");
        this.posts = response;
  },
  components: {
      post
  }
};
</script>

<style>
</style>