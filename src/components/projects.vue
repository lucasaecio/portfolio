<template>
  <v-container grid-list-xl>
    <v-layout wrap>
        <v-flex
        xs12
        sm6
        lg4

        v-for="project in projects"
        :key="project.id"
        >
            <v-card hover :href="project.url" height="100%">
                <v-img
                height="330px"
                src="https://avatars.githubusercontent.com/u/45777832?s=460&v=4"
                >
                </v-img>

                <v-divider />

                <v-card-text>
                    <h3 v-html="project.name" class="mb-2"></h3>
                    <v-chip
                    class="white--text mr-1"
                    color=info
                    small
                    v-for="tag in project.tags"
                    :key="tag.id"
                    >
                    {{ tag }}
                    </v-chip>
                </v-card-text>
            </v-card>
        </v-flex>
    </v-layout>
</v-container>
</template>

<script>
export default {
data () {
    return {
      projects: [
        { name: 'Spotify interface', url: `www.google.com`, tags: ['Javascript', 'Css', 'Html' ] },
        { name: 'Techno cursos', url: `www.google.com`, tags: ['Vue.js', 'Javascript', 'Css'] }
      ]
    }
  },
}
</script>

<style>

</style>