<template>
  <div class="main">
    <div class="text-center">
      <span class="title">BINARY TO DECIMAL</span>
      <div>
        <input
          v-model="binary"
          class="p-2 binary-input m-5"
          @keydown.enter="bin2Dec(binary)"
        />
        <button
          class="bg-light-blue-500 p-2 rounded-2xl text-white"
          @click="bin2Dec(binary)"
        >
          convert
        </button>
      </div>
      <span v-if="error">{{ error }}</span>
      <span v-if="result" class="text-center mt-3">Decimal: {{ result }}</span>

      <div class="flex justify-center" v-if="result">
        <table class="absolute">
          <tr>
            <th>Binário</th>
            <th>Operação</th>
            <th>Expoente</th>
            <th>Resultado</th>
          </tr>
          <tr v-for="(line, idx) of resolution" :key="idx">
            <td>{{ line.number }}</td>
            <td>*</td>
            <td>2 ^ {{ line.expo }}</td>
            <td>{{ line.result }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Binary',
  data() {
    return {
      test: 'Teste!',
      binary: '',
      result: 0,
      error: '',
      resolution: [],
    }
  },
  methods: {
    bin2Dec(binary) {
      this.result = 0
      this.error = ''
      this.resolution = []

      if (/[^0-1]/.test(binary)) {
        this.error =
          'Numero Inválido! Por favor, insira somente números binários (0 ou 1)'

        return
      }

      binary.split('').forEach((number, ix) => {
        const expo = binary.length - (ix + 1)
        const result = +number * Math.pow(2, expo)
        this.resolution.push({ number, expo, result })
        this.result += result
      })

      return this.result
    },
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

.title {
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
  font-size: 3rem;
  font-weight: bold;
  letter-spacing: 2px;
  text-align: center;
  color: #f35626;
  background-image: -webkit-linear-gradient(92deg, #f80000, #00aeff);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: hue 10s infinite linear;
}

table,
td,
th {
  margin-top: 30px;
  border: 1px solid rgb(14, 165, 233);
  padding: 10px;
}

table {
  border-collapse: collapse;
  border-radius: 20px;
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
