<template>
  <section id="endpoints">
    <div
      class="container bg-slate-400 mx-auto py-36 flex flex-col items-center space-y-6 shadow-lg rounded-md"
    >
      <h1 class="text-4xl font-bold">Test it out live!</h1>
      <div class="flex flex-col items-center space-y-6 w-full px-6">
        <form
          @submit.prevent="fetchData"
          class="flex flex-col items-center space-y-3 md:flex-row md:space-y-0 md:space-x-3"
        >
          <div class="flex items-center">
            <h2>https://nakamotonode.com/api/</h2>
            <input
              type="text"
              v-model="input"
              class="w-32 rounded-sm focus:outline-none"
            />
          </div>
          <button
            class="rounded-md px-2 py-1 w-16 bg-slate-800 text-white hover:scale-95"
          >
            GET
          </button>
        </form>
        <div v-if="loading" class="flex flex-col space-y-6 items-center">
          <h1>Loading...</h1>
          <div
            class="w-32 h-32 rounded-full border-blue-300 border-8 border-t-indigo-500 animate-spin"
          ></div>
        </div>
        <div
          v-else
          class="w-full bg-white p-5 rounded-md overflow-scroll max-h-96 min-h-[100px] md:w-1/2"
        >
          <pre>{{ res }}</pre>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {
      input: 'block/0',
      res: '',
      loading: false,
    }
  },
  methods: {
    async fetchData() {
      try {
        this.loading = true
        const res = await fetch(`https://nakamotonode.com/api/${this.input}`)
        this.res = await res.json()
      } catch (e) {
        this.res = 'Error!'
      }
      this.loading = false
    },
  },
})
</script>
