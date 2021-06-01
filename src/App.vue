<template>
  <div class="container mx-auto py-5 flex justify-center items-center h-screen">
    <Notification v-show="notification.message"></Notification>
    <div id="e-wallet" class="rounded overflow-hidden border bg-white">
      <div class="p-2 border-b pb-3">
        <span class="text-gray-500">Balance</span>
        <p class="text-5xl text-center">{{ balance }}$</p>
      </div>
      <div class="grid grid-cols-3">
        <Tab v-for="tab in tabs" :key="tab" :tab="tab" v-model:currentTab="currentTab"></Tab>
      </div>
      <Recharge v-show="currentTab === 'Recharge'"></Recharge>
      <Withdrawal v-show="currentTab === 'Withdrawal'"></Withdrawal>
      <History v-show="currentTab === 'History'"></History>
    </div>
  </div>
</template>

<script>
import Tab from './components/Tab'
import Recharge from './components/Recharge'
import Withdrawal from './components/Withdrawal'
import History from './components/History'
import Notification from './components/Notification'

export default {
  name: 'App',
  components: {
    Tab, Recharge, Withdrawal, History, Notification
  },
  created(){
    document.title = 'eWallet with Vue.js'
  },
  data() {
    return {
      balance: 0,
      tabs: ['Recharge', 'Withdrawal', 'History'],
      currentTab: 'Recharge',
      notification: {message: '', status: ''},
      history: []
    }
  },
  mounted() {
    document.body.classList.add('bg-gray-200')
  },
  unmounted() {
    document.body.classList.remove('bg-gray-200')
  },
  methods: {
    pushNotification({ message, status }) {
      this.notification = {message, status}
    },
    addHistory(method, amount) {
      this.history.unshift({ method, amount })
    },
  }
}
</script>
 
<style>
  #e-wallet {
    width: 400px; 
  }
</style>
