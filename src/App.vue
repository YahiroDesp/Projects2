<template>
  <div id="apps">
    <Markaform @getProducts="toGetProducts" /> 
    <Markaprod :products="products"/>
  </div>
</template>

<script>
import Markaform from '@/components/Markaform.vue'
import Markaprod from '@/components/Markaprod.vue'

export default {
  components: {
    Markaform,
    Markaprod
},

  data() {
    return {
      products: []
    }
  },

  methods: {
    toGetProducts(data) {
      this.products = data
    }
  }
}

</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Chivo Mono', sans-serif;
  font-weight: 400;
  overflow-x: hidden;
}

#app {
  padding: 20px 0;
}

#apps {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

</style>
