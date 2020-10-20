<template>

  <v-card class="mx-auto" max-width="344" outlined>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">{{ post.title }}</div>
        <v-list-item-subtitle>{{ post.body }}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
  </v-card>

</template>

<script>

export default {
    props: ["post"]
};

</script>

<style>
</style>