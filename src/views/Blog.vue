<template>
  <Title greeting="Hola desde mi blog"/>
  <!-- <button @click="consumirAPI">Consumir API</button> -->
  <div v-for="item in arrayBlog" :key="item.id">
    <router-link :to="`/blog/${item.id}`">
      {{ item.title }}
    </router-link>
  </div>
</template>

<script>
import Title from "../components/Title.vue";

export default {
  components: {
    Title
  },
  data() {
    return {
      arrayBlog: []
    }
  },
  methods: {
    async consumirAPI(){
      try {
        const data = await fetch('https://jsonplaceholder.typicode.com/posts')
        const array = await data.json()
        this.arrayBlog = array;
      } catch (error) {
        console.log(error)
      }
    }
  },
  created() {
    // No es recomendable usar funciones de flecha dentro de created
    this.consumirAPI()
  }
}
</script>

<style>

</style>