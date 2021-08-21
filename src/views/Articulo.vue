<template>
  <Title greeting="Mi entrada de Blog"/>
  <h2>Parámetro: {{ URL }} </h2>
  <h3>{{articulo.title}}</h3>
  <p>{{articulo.id}} - {{articulo.body}}</p>
</template>

<script>
import Title from "../components/Title.vue"

export default {
    name: 'Articulo',
    components: {
        Title
    },
    data() {
      return {
        URL: this.$route.params.id,
        articulo: {}
      }
    },
    methods: {
      async consumirArticulo() {
        try {
          const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.URL}`)
          const objeto = await data.json()
          this.articulo = objeto;
        } catch (error) {
          console.log(error)
        }
      }
    },
    created () {
      this.consumirArticulo()
    }
}
</script>

<style>

</style>