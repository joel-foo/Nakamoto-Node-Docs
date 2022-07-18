<template>
  <section id="intro">
    <div
      class="container bg-slate-400 mx-auto py-36 flex justify-around shadow-lg rounded-md"
    >
      <div class="flex flex-col space-y-20">
        <div class="flex flex-col justify-around items-center md:flex-row">
          <h1 class="text-4xl text-center font-semibold w-full md:w-1/3">
            What is this?
          </h1>
          <div class="w-full md:w-1/2 p-10">
            <ul class="list-disc">
              <li>
                This is a simple RESTful API designed to provide a convenient
                means to interface with your Bitcoin Core via the JSON-RPC
                interface.
              </li>
              <li>
                In other words, you can get statistics from your own node
                without relying on public block explorers which often track the
                addresses/transactions you are interested in. A further
                corollary of this means that if you have a raspberry pi or a
                spare computer lying around acting as a Bitcoin full node, you
                can set up a reverse proxy and have very own Bitcoin Core API up
                and running 24/7.
              </li>
            </ul>
            <a
              href="https://developer.bitcoin.org/reference/rpc/"
              target="_blank"
              class="underline"
              >More info on the JSON-RPC commands</a
            >
          </div>
        </div>
        <div class="flex flex-col justify-around items-center md:flex-row">
          <h1 class="text-4xl text-center font-semibold w-full md:w-1/3">
            Prerequisites
          </h1>
          <div class="w-full md:w-1/2 p-10">
            <ul class="list-disc">
              <li>You need to run a full node (non-pruned)</li>
              <li>
                Edit your bitcoin.conf file located in the relevant directory
                listed
                <a
                  href="https://en.bitcoin.it/wiki/Running_Bitcoin"
                  target="_blank"
                  class="underline"
                  >here</a
                >
                depending on your filesystem because you would require
                credentials and additional configurations to use the RPC
                interface
              </li>
              <li>
                You are strongly recommended to run "txindex=1", as you would
                not be able to use endpoints such as "txout, txoutset" if you do
                not do so. Reindexing would take a few hours, assuming starting
                from an unindexed full node. *Note that these commands typically
                take a long time to respond (usually a few minutes). If you wish
                for something faster, run your own Electrum server/query an
                Electrum server.*
              </li>
            </ul>
          </div>
        </div>
        <div class="flex flex-col justify-around items-center md:flex-row">
          <h1 class="text-4xl text-center font-semibold w-full md:w-1/3">
            Installing from source
          </h1>
          <div class="w-full md:w-1/2 p-10">
            <img
              src="../assets/install-from-source.png"
              alt=""
              class="rounded-md"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
