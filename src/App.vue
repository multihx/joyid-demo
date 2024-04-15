<template>
  <div class="flex flex-col h-screen">
    <button @click="login">login</button>
    <button @click="sign">sign</button>
  </div>
</template>

<script>
// import Navbar from "./components/Navbar.vue"

import { connect, signTransaction } from '@joyid/ckb'

export default {
  data() {
    return {
      authData: null,
    }
  },
  methods: {
    async login() {
      const connectData = await connect()
      console.log(connectData)

      this.authData = connectData
    },
    async sign() {
      const signedTx1 = await signTransaction({
        to: 'ckt1qpuljza4azfdsrwjzdpea6442yfqadqhv7yzfu5zknlmtusm45hpuqgp2ah0f8q3prdddylcqfacgl5f0fvy98feqqmn78cj',
        from: this.authData.address,
        amount: 13000000000,
      })
      let signedTx2 = JSON.stringify(signedTx1)
      console.log('signedTx', signedTx2)
    },
  },
  components: {
    // Navbar,
  },
}
</script>
