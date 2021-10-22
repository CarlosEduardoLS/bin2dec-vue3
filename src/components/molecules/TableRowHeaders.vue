<template>
  <tr>
    <TableHeader v-for="header of headers" :key="header" :text="header" />
  </tr>
</template>

<script>
import TableHeader from '@/components/atoms/TableHeader'

export default {
  name: 'TableRowHeaders',
  components: {
    TableHeader,
  },
  props: {
    headers: {
      type: Array,
      required: true,
    },
  },
  setup() {},
}
</script>
