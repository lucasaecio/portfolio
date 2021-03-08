<template>
  <div class="home">
    <v-app>
      <Header/>
      <Projects/>
    </v-app>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/header.vue'
import Projects from '@/components/projects.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Projects
  }
}
</script>
