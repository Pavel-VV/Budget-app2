<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <template v-if="!isEmpty">
        <div v-for="(item, prop) in list" :key="prop">
          <BudgetListItem :listItem="item" @deleteItem="onDeleteElement"/>
        </div>
      </template>
      <ElAlert v-else type="info" :title="emptyTitle" :closable="false"/>


    </ElCard>
  </div>

</template>

<script>
import BudgetListItem from '@/components/BudgetListItem';

export default {
  name: 'BudgetList',
  components: {
    BudgetListItem,
  },
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
    onDeleteElement(id) {
      this.$emit('deleteItemInApp', id);
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
</style>
