<template>
  <v-app dark>
    <v-toolbar fixed>
      <v-toolbar-title v-text="title">E_Auction</v-toolbar-title>
    </v-toolbar>
    <main>
      <v-alert error value="true" v-if="!metamask">
        This application requires the MetaMask Chrome Plugin
      </v-alert>
      <v-container v-if="metamask">
        <v-layout row>
          <wallet-info></wallet-info>
          <send-tokens></send-tokens>
        </v-layout>
      </v-container>
    </main>
    <v-footer fixed>
      <span>&copy; 2019 - E_Auction</span>
    </v-footer>
  </v-app>
</template>

<script>
import WalletInfo from './components/WalletInfo.vue'
import SendTokens from './components/SendTokens.vue'

export default {

  components: {
    WalletInfo,
    SendTokens
  },

  data () {
    return {
      title: 'Func Wallet'
    }
  },

  computed: {
    metamask () {
      return window['web3'] !== undefined
    }
  }

}
</script>

<style lang="stylus">
  @import './stylus/main'
</style>
