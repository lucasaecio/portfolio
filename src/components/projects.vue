<template>
  <v-container grid-list-xl>
    <v-layout class="project-list" wrap>
        <v-flex
        xs12
        sm6
        lg3
        xl3

        v-for="project in projects"
        :key="project.id"
        >
            <v-card hover :href="project.url" target="_blank" height="100%">
                <v-img
                height="280px"
                src="https://avatars.githubusercontent.com/u/45777832?s=460&v=4"
                >
                </v-img>

                <v-divider />

                <v-card-text>
                    <h3 v-html="project.name" class="mb-2"></h3>
                    <v-chip
                    class="white--text mr-1 mt-1"
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
        ]
        }
    },
    methods: {
        getReposGitHub() {
            fetch('https://api.github.com/users/lucasaecio/repos?sort="updated"')
            .then(response => response.json())
            .then(data => {
                data.map((value) => {
                    let projectDescription = {};
                    projectDescription['id'] = value.id;
                    projectDescription['name'] = value.name;
                    projectDescription['url'] = `https://lucasaecio.github.io/${value.name}`;
                    projectDescription['tags'] = [];

                    fetch(value.languages_url)
                    .then(response => response.json())
                    .then(data => {
                        Object.entries(data).forEach(
                            ([language]) => projectDescription['tags'].push(language)
                        );
                    })

                    this.projects.push(projectDescription);
                })
            })
        }
    },
    created(){
        this.getReposGitHub()
    }
}
</script>

<style scoped>
.project-list {
    margin: 0 auto !important;
    max-width: 1170px !important;
}
</style>