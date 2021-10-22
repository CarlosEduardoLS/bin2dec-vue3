<template>
  <input
    :value="value"
    class="p-2 binary-input m-5"
    @input="updateValue"
    @keydown.enter="changeHandler"
  />
</template>

<script lang="js">
import { computed } from '@vue/reactivity'

export default {
  name: 'TextInput',
  emits: ['input', 'keydown'],
  props: {
    value: {
      type: String,
      required: true
    },
  },
  setup(props, { emit }) {
    const val = computed({
      get: () => props.value,
      set: v => {
        console.log('V -> ', v)
        emit('input', v)
      }
    })

    function updateValue(v) {
      emit('input', v.data)
    }

    function changeHandler() {
      emit('keydown', props.value)
    }

    return {
      val,
      changeHandler,
      updateValue
    }
  },
}
</script>
