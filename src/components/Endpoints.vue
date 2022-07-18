<template>
  <section id="endpoints">
    <div class="container bg-slate-500 mx-auto py-36">
      <div class="flex flex-col space-y-20 justify-center">
        <h1 class="text-center text-4xl text-white px-5">
          All endpoints are prefixed by /api
        </h1>
        <div
          :class="[
            'flex flex-col space-y-10 items-center px-2 md:flex-row md:px-20',
            i % 2 !== 0 && 'md:flex-row-reverse',
          ]"
          v-for="(e, i) in endpoints"
          :key="i"
        >
          <div
            class="w-full flex flex-col space-y-6 items-center px-10 text-white md:w-1/2"
          >
            <h1 class="text-4xl">{{ e }}</h1>
            <div v-if="i === 3" class="flex flex-col space-y-3 text-center">
              <h2 class="text-xl">Also supports: {{ e }}?q={field}</h2>
              <p>
                field =
                <span v-for="(f, i) in fields" :key="i">{{ f }} </span>
              </p>
            </div>
            <div v-if="i === 5" class="flex flex-col space-y-3 text-center">
              <p>
                type =
                <span v-for="(t, i) in typeTxout" :key="i">{{ t }} </span>
              </p>
              <p>
                val =
                <span v-for="(v, i) in valueTxout" :key="i">{{ v }} </span>
              </p>
            </div>
            <p v-if="i <= 2">h = block height | block hash</p>
            <p class="max-w-md text-amber-100">{{ descriptions[i] }}</p>
          </div>
          <img :src="getImageUrl(i)" alt="" class="w-sm rounded-md md:w-1/2" />
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
      endpoints: [
        '/block/{h}',
        '/header/{h}',
        '/blockstats/{h}',
        '/blockchaininfo',
        '/txout/{txid}/{vout}',
        '/txoutset/{type}/{val}',
        '/alltxoutset',
      ],
      fields: [
        'blockcount | ',
        'bestblockhash | ',
        'difficulty | ',
        'softforks',
      ],
      descriptions: [
        'returns block info',
        'returns block header info',
        'returns block stats',
        'returns general overview of blockchain',
        'retrieves the UTXO given a TxID and its position (vout) in that associated transaction',
        'returns all UTXOs and thus total value associated with a given address/pubkey',
        'scans the entire UTXO set and returns the total no. of transactions with UTXOs, the total no. of UTXOs and the total value corresponding to said UTXOs',
      ],
      src: [
        'https://nakamotonode.com/api/block/0',
        'https://nakamotonode.com/api/header/0',
        'https://nakamotonode.com/api/blockstats/500000',
        'https://nakamotonode.com/api/blockchaininfo',
      ],
      img: [
        'block-0',
        'header-0',
        'stats-500k',
        'blockchaininfo',
        'txout-sample',
        'txoutset-sample',
        'alltxoutset',
      ],
      typeTxout: [
        'addr | ',
        'raw | ',
        'combo | ',
        'pkh',
        // 'sh | ',
      ],
      valueTxout: [
        '<address> | ',
        '<hex script> | ',
        '<pubkey> | ',
        '<pubkey>',
        //multi(<n>,<pubkey>,<pubkey>,…) | ',
      ],
    }
  },
  methods: {
    fetchData() {},
    getImageUrl(i: number) {
      return new URL(`../assets/${this.img[i]}.png`, import.meta.url).href
    },
  },
})
</script>
