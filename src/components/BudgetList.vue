<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <template v-if="!isEmpty">
        <div class="list-item" v-for="(item, prop) in list" :key="prop">
          <span class="budget-comments">{{ item.comments }}</span>
          <span class="budget-value">{{ item.value }}</span>
          <ElButton type="danger" size="mini" @click="deleteElement(item.id)">Delete</ElButton>
        </div>
      </template>
      <ElAlert v-else type="info" :title="emptyTitle" :closable="false"/>


    </ElCard>
  </div>

</template>

<script>
export default {
  name: 'BudgetList',
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    header: 'Budjet List',
    emptyTitle: "Empty List",
  }),
  methods: {
    deleteElement(id) {
      this.$emit('deleteItem', id);
    },
  },
  computed: {
    isEmpty() {
      return !Object.keys(this.list).length
    },
  }
}
</script>

<style scoped>
.budget-list-wrap {
  max-width: 500px;
  margin: auto;
}

.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;
}

.budget-value {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}

</style>
