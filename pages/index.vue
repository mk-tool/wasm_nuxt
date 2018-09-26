<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title" @click="callGreet">
        wasm-nuxt
      </h1>
      <h2 class="subtitle">
        My ultimate Nuxt.js project
      </h2>
      <div class="links">
        <a
          @click="callGreet"
          class="button--green"
        >click me</a>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue';
const myWasmModule = import("~/assets/js_hello_world");

export default {
  components: {
    Logo
  },
  data() {
    return { 
      myName: 'mk-tool'
    }
  },
  methods: {
    callGreet() {
      myWasmModule.then(myWasmModule => myWasmModule.greet(this.myName));
    },
  },
}
</script>

<style>

.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
