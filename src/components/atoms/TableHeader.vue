<template>
  <th>{{ text }}</th>
</template>

<script>
export default {
  name: 'TableHeader',
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  setup() {},
}
</script>

<style scoped>
th {
  margin-top: 30px;
  border: 1px solid rgb(14, 165, 233);
  padding: 10px;
}
</style>
