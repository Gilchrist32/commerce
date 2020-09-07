<template>
  <v-app :style="mode ? 'background-color: #f7f7f7;' : 'background-color: #363636;'">
    
    <v-content>
      <router-view />
    </v-content>

    <Footer />

    <BackToTop />
  </v-app>
</template>

<script>
import { mapState } from 'vuex'
import BackToTop from './components/mixin/BackToTop';
import Footer from '@/components/layout/Footer.vue'

export default {
  name: 'App',

  components: {
    BackToTop,
    Footer
  },

    computed: {
      ...mapState(['mode'])
    }
};
</script>
