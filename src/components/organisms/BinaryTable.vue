<template>
  <table class="absolute">
    <TableRowHeaders :headers="headers" />
    <TableRowDatas
      v-for="data of datas"
      :key="data"
      :datas="[`${data.number}`, '*', `2 ^ ${data.number}`, `${data.result}`]"
    />
  </table>
</template>

<script>
import TableRowHeaders from '@/components/molecules/TableRowHeaders'
import TableRowDatas from '@/components/molecules/TableRowDatas'

export default {
  name: 'BinaryTable',
  props: {
    headers: {
      type: Array,
      required: true,
    },
    datas: {
      type: Array,
      required: true,
    },
  },
  components: {
    TableRowHeaders,
    TableRowDatas,
  },
  setup() {},
}
</script>

<style scoped>
table {
  border-collapse: collapse;
  border-radius: 20px;
  margin-top: 30px;
  border: 1px solid rgb(14, 165, 233);
  padding: 10px;
}
</style>
