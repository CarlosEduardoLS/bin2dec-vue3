<template>
  <span class="text-center mt-3">{{ text }}</span>
</template>

<script>
export default {
  name: 'TextSpan',
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  setup() {},
}
</script>
