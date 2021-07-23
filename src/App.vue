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
    }
    window.top.postMessage(message, '*')
    window.addEventListener('message', this.onMessage, false)
    window.addEventListener('resize', this.onResize, false)
    this.onResize();
  },

  methods: {
    onMessage(e){
      let message = e.data;
      switch (message.name) {
        case 'init-locale':
          this.$i18n.locale = message.locale;
          break;
        case 'locale-change':
          this.$i18n.locale = message.locale;
          break;
      }
    },
    onReceivedSessionData(e) {
      let data = e.detail;
    },
    onResize(){
      let message = {
        'name': 'on-resize',
        'height': document.getElementById('app').offsetHeight
      }
      window.top.postMessage(message, '*')
    }
  }

}
</script>


<style lang="scss">
body {
  overflow: hidden; /* Hide scrollbars */
}
</style>
