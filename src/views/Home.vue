<template>
  <div class="home">
    <Title greeting="Bienvenido al Blog de Vue"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Title from "../components/Title.vue"

export default {
  name: 'Home',
  components: {
   Title
  }
}
</script>
