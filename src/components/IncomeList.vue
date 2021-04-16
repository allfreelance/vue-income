<template>
  <div class="income-list">
    <IncomeItem v-for="data in state.income" :key="data.id" :income="data"  @delete-item="deleteItem"></IncomeItem>
  </div>
</template>
<script>
import IncomeItem from './IncomeItem'

export default {
  components: { IncomeItem },
  props: {
    state: Object
  },
  setup(props, { emit }) {
    function deleteItem(item) {
      emit("deleteItem", item)
    }
    return {
      IncomeItem,
      deleteItem
    }
  }
}
</script>
<style scoped>
  .income-list {
    margin-top: 30px;
    padding: 15px;
  }
</style>