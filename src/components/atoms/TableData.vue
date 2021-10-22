<template>
  <td>{{ text }}</td>
</template>

<script>
export default {
  name: 'TableData',
  props: {
    text: {
      type: [String, Number],
      required: true,
    },
  },
  setup() {},
}
</script>

<style scoped>
td {
  margin-top: 30px;
  border: 1px solid rgb(14, 165, 233);
  padding: 10px;
}
</style>
