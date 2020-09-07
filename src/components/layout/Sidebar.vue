<template>
    <v-navigation-drawer v-model="show" app temporary dark>
      <v-list>
        <v-list-item>
          <v-list-item-avatar>
            <img src="@/assets/logo.png" alt="Logo" />
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="title font-weight-light ">Shopify</v-list-item-title>
            E-Commerce
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider />

      <v-list>
        <v-list-item
          v-for="([icon, text, link], i) in items"
          :key="i"
          link
          @click="$vuetify.goTo(link)"
        >
          <v-list-item-icon class="justify-center">
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">
                {{text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
            <v-btn rounded outlined text block large>
                <v-icon medium left>mdi-account-circle</v-icon>
                <span class="mr-2">Sign In</span>
            </v-btn>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
</template>

<script>
    export default {
        name: 'Sidebar',
        
        props: ['items', 'visible'],
        computed: {
            show: {
                get (){
                    return this.visible
                },
                set (value) {
                    if (!value) {
                        this.$emit('close')
                    }
                }
            }
        }
    }
</script>