<template>
  <form class="p-5" @submit.prevent="recharge">
		<label class="text-gray-500 mb-1 block">Enter the amount</label>
		<input type="number" class="px-3 py-1 border rounded w-full text-2xl" 
			v-model="amount" v-model.number="amount">
		<button type="submit" class="py-2 bg-green-500 hover:bg-green-600 focus:outline-none text-white block w-full rounded mt-3">Submit</button>
	</form>
</template>

<script>
export default {
	name: 'Recharge',
	data() {
		return {amount: 0}
	},
	methods: {
		recharge() {
      if (this.amount == 0) return false;

			this.$parent.balance += + this.amount
      this.$parent.addHistory('recharge', this.amount)
			this.amount = 0

      this.$parent.pushNotification({
        'message': 'Recharged successfuly!',
        'status': 'success'
      })
		}
	}
};
</script>
