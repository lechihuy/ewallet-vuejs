<template>
  <div class="text-center py-3 cursor-pointer hover:bg-gray-100"
    :class="[{'font-bold text-blue-500': currentTab === tab}]"
    @click="activeTab(tab)"
  >{{ tab }}</div>
</template>

<script>
export default {
  name: "Tab",
  props: {
    tab: String,
    currentTab: String
  },
  methods: {
    activeTab(tab) {
      this.$emit('update:currentTab', tab);
    }
  }
};
</script>
