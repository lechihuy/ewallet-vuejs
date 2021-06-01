<template>
  <div id="notification" class="bg-white shadow-md border rounded-md flex p-3 fixed top-5 right-5">
    <span v-html="getStatusIcon()"></span>
    <div class="ml-3 flex-grow">
      <h3 class="font-bold text-sm">{{ getStatusText() }}</h3>
      <p class="text-gray-500 text-sm">{{ $parent.notification.message }}</p>
    </div>
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-500 cursor-pointer" fill="none" viewBox="0 0 24 24" stroke="currentColor"
      @click="$parent.notification.message = ''"
    >
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
    </svg>
  </div>  
</template>

<script>
const statusText = {
  success: 'OK',
  error: 'Oops'
}

const statusIcon = {
  success: `
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  `,
  error:  `
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-red-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  `
}

export default {
  name: 'Notification',
  methods: {
    getStatusText() {
      return statusText[this.$parent.notification.status]
    },
    getStatusIcon() {
      return statusIcon[this.$parent.notification.status]
    }
  }
}
</script>


<style scoped>
  #notification {
    width: 300px;
  }
</style>