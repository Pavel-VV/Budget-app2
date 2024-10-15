<template>
  <div class="list-item">
    <span class="budget-coment">{{ listItem.comment }}</span>
    <span class="badget-value">{{ listItem.value }}</span>
    <ElButton type="danger" size="mini" @click="deleteElement(listItem.id)">Delete</ElButton>
  </div>
</template>

<script>
export default {
  name: 'BudgetListItem',
  props: {
    listItem: {
      type: Object,
      default: () => ({}),
    }
  },
  methods: {
    deleteElement(id) {
      let result = confirm(`Вы действительно хотите удалить: "${this.listItem.comment}"?`);
      if(result) this.$emit('deleteItem', id);
    },
  }

}
</script>

<style scoped>
.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;

}

.badget-value {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}
</style>
