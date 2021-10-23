<template>
  <input :value="modelValue" class="p-2 binary-input m-5" @input="updateValue" />
</template>

<script lang="js">
export default {
  name: 'TextInput',
  emits: ['update:modelValue'],
  props: {
    modelValue: {
      type: [String,Number],
      required: true
    },
  },
  setup(props, { emit }) {
    function updateValue(v) {
      emit('update:modelValue', v.target.value)
    }

    return {
      updateValue
    }
  },
}
</script>
