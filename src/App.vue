<template>
  <section id="home">
    <div
      class="container bg-slate-500 mx-auto py-36 px-20 flex flex-col items-center space-y-10 relative"
    >
      <h1 class="text-4xl text-white font-bold">Nakamoto Node</h1>
      <h3 class="text-honeydew italic">
        A simple RESTful Bitcoin Core API designed with NodeJS
      </h3>
      <a
        href="https://github.com/joel-foo/bitcoin-api"
        target="_blank"
        class="absolute right-8 -top-5"
      >
        <ion-icon name="logo-github" class="text-4xl text-white"></ion-icon
      ></a>
    </div>
  </section>
  <About />
  <Endpoints />
  <Test />
  <section id="contact">
    <div class="container bg-slate-500 mx-auto py-36">
      <h1 class="text-4xl text-center text-white">&copy; Joel Foo 2022</h1>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Endpoints from './components/Endpoints.vue'
import About from './components/About.vue'
import Test from './components/Test.vue'

export default defineComponent({
  data() {
    return {}
  },
  components: { Endpoints, About, Test },
})
</script>
