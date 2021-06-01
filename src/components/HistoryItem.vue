<template>
  <li class="flex justify-between p-2"
    :class="[index % 2 === 0 ? 'bg-gray-100' : '']"
  >
    <span>{{ item.method === 'recharge' ? 'Recharged' : 'Withdrawn' }}</span>
    <span class="flex items-center"
      :class="item.method === 'recharge' ? 'text-green-500' : 'text-red-500'"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-3 w-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"
        v-if="item.method === 'recharge'"
      >
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
      </svg>
      <svg xmlns="http://www.w3.org/2000/svg" class="h-3 w-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"
        v-if="item.method === 'withdrawal'"
      >
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
      </svg>
      {{ item.amount }}$
    </span>
  </li>
</template>

<script>
export default {
	name: 'HistoryItem',
  props: {
    item: Object,
    index: Number
  }
};
</script>