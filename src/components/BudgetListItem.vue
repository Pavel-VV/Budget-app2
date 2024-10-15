<template>
  <div class="list-item">
    <span class="budget-coment">{{ listItem.comment }}</span>
    <span class="badget-value">{{ listItem.value }}</span>
    <!-- <ElButton type="danger" size="mini" @click="deleteElement(listItem.id)">Delete</ElButton> -->
    <ElButton type="danger" size="mini" @click="dialogDeleteVisible = true">Delete</ElButton>

    <ElDialog title="Warning" :visible.sync="dialogDeleteVisible" width="30%" center>
      <span>Вы действительно хотите удалить: "{{ listItem.comment }}"?</span>
      <span slot="footer" class="dialog-footer">
        <ElButton @click="dialogDeleteVisible = false">Cancel</ElButton>
        <ElButton type="danger" @click="deleteElementDialog(listItem.id)">Ok</ElButton>
      </span>
    </ElDialog>
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
  data: () => ({
    dialogDeleteVisible: false,
  }),
  methods: {
    deleteElement(id) {
      let result = confirm(`Вы действительно хотите удалить: "${this.listItem.comment}"?`);
      if(result) this.$emit('deleteItem', id);
    },
    deleteElementDialog(id) {
      this.$emit('deleteItem', id);
      this.dialogDeleteVisible = false;
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
