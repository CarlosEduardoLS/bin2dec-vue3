<template>
  <button class="bg-light-blue-500 p-2 rounded-2xl text-white" @click="handleClick">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'PrimaryButton',
  emits: ['click'],
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  setup(props, { emit }) {
    function handleClick(v) {
      emit('click', v)
    }

    return {
      handleClick,
    }
  },
}
</script>
