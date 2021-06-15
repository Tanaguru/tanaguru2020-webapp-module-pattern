<template>
  <div id="app">
    <home/>
  </div>
</template>

<script>
import Home from "@/views/Home";
export default {
  name: 'App',
  components: {Home},
  mounted() {
    let message = {
      'name': 'on-module-mounted',
      'height': document.getElementById('app').offsetHeight
    }
    window.top.postMessage(message, '*')

  },

  methods: {
    onReceivedSessionData(e) {
      let data = e.detail;
      console.log(data)
    }
  }

}
</script>


<style lang="scss">
@import "~tanaguru-vue/src/scss/style";
</style>
