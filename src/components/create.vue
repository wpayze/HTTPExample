<template>
  <v-container>

    <div class="label-success" v-if="estado == true">
      TODO FUE UN EXITO FELICIDADES
    </div>

    <div class="label-error" v-if="estado == false">
      ESTO NO SIRVIO NI PIJA
    </div>

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
      estado: null
    };
  },
  methods: {
      async guardar() {

        const { data: response } = await axios.post("https://jsonplaceholder.typicode.com/posts", 
        {
            title: this.title,
            body: this.body
        });

        if ( !response.id ) {
          this.$toast.success("FELICIDADES !!!!");
          //this.$router.push("/");
          this.estado = true;
        } else {
          this.$toast.error("ESTO NO SIRVIO");
          this.estado = false;
        }

        var instancia = this;
        setTimeout( () => {
          instancia.estado = null;
        }, 2000);
      }
  }
};
</script>

<style>
  .label-success {
    background: green;
    color: #fff;
    padding: 1em;
  }

  .label-error {
    background: red;
    color: #fff;
    padding: 1em;
  }
</style>