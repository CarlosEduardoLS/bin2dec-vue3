<template>
  <tr>
    <TableData v-for="data of datas" :key="data" :text="data" />
  </tr>
</template>

<script>
import TableData from '@/components/atoms/TableData'

export default {
  name: 'TableRowDatas',
  props: {
    datas: {
      type: Array,
      required: true,
    },
  },
  components: {
    TableData,
  },
  setup() {},
}
</script>
