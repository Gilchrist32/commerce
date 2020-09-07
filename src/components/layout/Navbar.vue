<template>
  <div>
    <v-app-bar app dark prominent extended class="px-0"
    src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg">
      
      <v-toolbar-title class="text-uppercase white--text">
        <span>Shopify  </span>
        <span class="font-weight-light">E-Commerce</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
      </v-toolbar-title>
      
      <v-spacer />

      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="mr-4"
        v-if="isXs"
      />
      
      <div v-else>
        <v-btn text @click="$vuetify.goTo('#hero')" rounded>
          <span class="mr-2">Home</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#about')" rounded>
          <span class="mr-2">About</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#services')" rounded>
          <span class="mr-2">Services</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#contact')" rounded>
          <span class="mr-2">Contact</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#cart')" rounded>
          <v-badge left color="green">
            <span slot="badge">0</span>
            <v-icon>shopping_cart</v-icon>
            <span class="mr-2">Cart</span>
          </v-badge>
        </v-btn>
        <v-btn rounded depressed outlined text color="primary darken-1">
          <span >Sign In</span>
        </v-btn>
        <Search />
      </div>
      <br>

    </v-app-bar>
    
    <Sidebar
        :visible="drawer"
        :items="items"
        @close="drawer = false"
        
    />

  </div>
</template>

<script>
    export default {
        components: {
            Sidebar: () => import('./Sidebar'),
            Search: () => import('@/components/mixin/Search')
        },
        data () {
            return {
                drawer: false,
                isXs: false,
                items: [
                    ["mdi-cube-outline", "Home", "#hero"],
                    ["mdi-information-outline", "About", "#about"],
                    ["mdi-folder-outline", "Services", "#services"],
                    ["mdi-cellphone-dock", "Contact", "#contact"],
                ]
            }
        },
        methods: {
            onResize () {
                this.isXs = window.innerWidth < 850;
            }
        },
        watch: {
            isXs (value) {
                if (!value) {
                    if (this.drawer) {
                        this.drawer = false;
                    }
                }
            }
        },
        mounted() {
            this.onResize()
            window.addEventListener("resize", this.onResize, { 
                passive: true 
            })
        }
    }
</script>

<style scoped>
    .v-toolbar {
        transition: 0.6s;
    }
    .expand {
        height: 80px !important;
        padding-top: 10px;
    }
</style>