<template>
  <div id="home">

    <Navbar />
    
    <Mainbar>

    </Mainbar>


  </div>
</template>

<script>
import Navbar from '@/components/layout/Navbar.vue'
import Mainbar from '@/components/layout/Mainbar.vue'

export default {
  name: 'Shopify',
  components: {
    Navbar,
    Mainbar,
  }
}
</script>
