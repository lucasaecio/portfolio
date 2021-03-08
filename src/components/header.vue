<template>
  <section class="main">
<!-- 
        <v-btn icon href="https://www.linkedin.com/in/lucasaecio" target="_blank" right>
        <i class="fab fa-linkedin"></i>
        </v-btn>

        <v-btn icon href="https://github.com/lucasaecio" target="_blank" right>
        <i class="fab fa-github" ></i>
        </v-btn> -->
        <v-container fluid fill-height grid-list-xl>
            <v-layout row wrap align-center>

                <v-flex>
                        <v-card class="text-center" id="description-card" flat dark>
                            <h1 class="display-2 mb-3">Lucas Aécio - Projetos</h1>
                            <h2>
                            Desenvolvidos durante cursos e aprendizados...
                            <em style="display:block;font-size:1rem;">- Java, Vue.js, Vuetify, Bootstrap, PHP, HTML, CSS, MySQL etc.</em>
                            </h2>
                        </v-card>
                </v-flex>

                    <v-flex>
                        <v-container class="text-center">
                            <transition mode="out-in">
                                <v-avatar
                                class="grey lighten-4"
                                v-if="isAvatarVisible"
                                :size="avatarSize"
                                >
                                    <img :src="avatarUrl" />
                                </v-avatar>
                            </transition>
                        </v-container>
                    </v-flex>

            </v-layout>
        </v-container>
</section>
</template>

<script>
export default {
    name: "Header",
    data () {
        return {
            avatarSize: 250,
            isAvatarVisible: false,
            avatarUrl: null
        }
    },
    methods: {
        getGitUserProfile() {
            fetch('https://api.github.com/users/lucasaecio')
            .then((response) => response.json())
            .then(data => {
                this.avatarUrl = data.avatar_url
            })
        }
    },
     mounted () {
        // To trigger animation
        this.isAvatarVisible = true;
    },
    created() {
        this.getGitUserProfile()
    }
}
</script>

<style scoped>
section.main {
    background: linear-gradient(to right, #004, #1CB5E0);
    padding: 12px 0;
}

#description-card {
    background: transparent;
}

div.flex,
div.container.text-center {
    padding-top: 0 !important;
}


/* Animation */
.v-enter-active, .v-leave-active {
  transition: all 1s ease;
}

.v-enter, .v-leave-to {
  transform: scale(0.1);
  opacity: 0;
}
</style>