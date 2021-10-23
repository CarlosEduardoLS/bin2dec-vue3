<template>
  <div class="main">
    <div class="text-center">
      <GradientTitle title="Binary to Decimal" />

      <form @submit.prevent="bin2Dec">
        <TextInput v-model="binary" />
        <PrimaryButton text="convert" />
      </form>

      <TextSpan :text="error" />
      <TextSpan v-if="result" :text="`Decimal: ${result}`" />

      <FlexTable v-if="result" :headers="headers" :datas="resolution" />
    </div>
  </div>
</template>

<script lang="js">
import { ref } from '@vue/reactivity'
import GradientTitle from '@/components/atoms/GradientTitle'
import PrimaryButton from '@/components/atoms/PrimaryButton'
import TextSpan from '@/components/atoms/TextSpan'
import TextInput from '@/components/atoms/TextInput'
import FlexTable from '@/components/bosons/FlexTable'

export default {
  components: {
    GradientTitle,
    PrimaryButton,
    TextSpan,
    TextInput,
    FlexTable,
  },
  name: 'BinaryTemplate',
  setup() {
    let binary = ref('')
    let result = ref(0)
    let error = ref('')
    let resolution = ref([])
    const headers = ['Binário', 'Operação', 'Expoente', 'Resultado']

    function bin2Dec() {
      this.result = 0
      this.error = ''
      this.resolution = []

      if (/[^0-1]/.test(binary.value)) {
        this.error =
          'Numero Inválido! Por favor, insira somente números binários (0 ou 1)'

        return
      }

      binary.value.split('').forEach((number, ix) => {
        const expo = binary.value.length - (ix + 1)
        const result = +number * Math.pow(2, expo)
        this.resolution.push({ number, expo, result })
        this.result += result
      })

      return this.result
    }

    return {
      binary,
      result,
      error,
      resolution,
      bin2Dec,
      headers
    }
  },
}
</script>

<style scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  min-height: -webkit-fill-available;
}

.binary-input {
  border: 1px solid rgb(14, 165, 233);
  border-radius: 15px;
}

@keyframes hue {
  from {
    -webkit-filter: hue-rotate(0deg);
  }
  to {
    -webkit-filter: hue-rotate(-360deg);
  }
}
</style>
