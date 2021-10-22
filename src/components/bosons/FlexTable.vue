<template>
  <div class="flex justify-center">
    <BinaryTable :headers="headers" :datas="datas" />
  </div>
</template>

<script>
import BinaryTable from '@/components/organisms/BinaryTable'

export default {
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
    BinaryTable,
  },
  setup() {},
}
</script>
