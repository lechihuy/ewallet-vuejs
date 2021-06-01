<template>
  <div class="p-5">
    <ul v-show="$parent.history.length">
      <HistoryItem v-for="(item, index) in $parent.history" :key="index" :index="index"
        :item="item"
      ></HistoryItem>
    </ul>
    <p class="text-center italic" v-if="! $parent.history.length">No item</p>
  </div>

</template>

<script>
import HistoryItem from './HistoryItem'

export default {
	name: 'History',
  components: {
    HistoryItem
  }
};
</script>
