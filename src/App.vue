<template>
  <div id="app">
    <FormData/>
    <TotalBalance :total="totalBalance"/>
    <BudgetList :list="list" @deleteItem="onDeleteItem"/>
  </div>
</template>

<script>
import BudgetList from '@/components/BudgetList';
import TotalBalance from '@/components/TotalBalance';
import FormData from '@/components/FormData';

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    FormData,
  },
  data: () => ({
    list: {
      1: {
        type: 'INCOME',
        value: 100,
        comments: 'Some comment',
        id: 1,
      },
      2: {
        type: 'OUTCOME',
        value: -50,
        comments: 'Some outcome comment',
        id: 2,
      },
    }
  }),
  methods: {
    onDeleteItem(id) {
      this.$delete(this.list, id);
    }
  },
  computed: {
    totalBalance() {
      return Object.values(this.list).reduce((acc, el) => {
        return acc + el.value;
      }, 0)
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
