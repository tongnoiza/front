<template>
  <v-app dark>
    <v-main>
   <Vwinsows/>
      <v-container>
        <Nuxt />
      </v-container> 
    </v-main>
    <footer> <Footer/></footer>
  </v-app>
</template>

<script>
import Footer from "../components/Footer.vue";
export default {
  layout:'default',
    name: "DefaultLayout",
    data() {
        return {
            length: 3,
            onboarding: 0,
            clipped: false,
            drawer: false,
            fixed: false,
            items: [
                {
                    icon: "mdi-apps",
                    title: "Welcome",
                    to: "/"
                },
                {
                    icon: "mdi-chart-bubble",
                    title: "Inspire",
                    to: "/inspire"
                }
            ],
            miniVariant: false,
            right: true,
            rightDrawer: false,
            title: "Vuetify.js"
        };
    },
  
    methods: {

    },
    components: { Footer }
}
</script>
