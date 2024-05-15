<template>
  <div class="conversion-container">
    <div class="conversion-box">
      <h1>Conversiones de Temperatura</h1>
      <table class="input-table">
        <tbody>
          <tr>
            <td class="input-label"><label for="inputValue">Valor a convertir:</label></td>
            <td><input type="number" v-model="inputValue" @input="convertir" id="inputValue" class="input-field"></td>
          </tr>
          <tr>
            <td class="input-label"><label for="unidadOrigen">Desde:</label></td>
            <td><select v-model="unidadOrigen" @change="convertir" id="unidadOrigen" class="select-box">
              <option value="celsius">Celsius (°C)</option>
              <option value="fahrenheit">Fahrenheit (°F)</option>
              <option value="kelvin">Kelvin (K)</option>
            </select></td>
          </tr>
          <tr>
            <td class="input-label"><label for="unidadDestino">Hacia:</label></td>
            <td><select v-model="unidadDestino" @change="convertir" id="unidadDestino" class="select-box">
              <option value="celsius">Celsius (°C)</option>
              <option value="fahrenheit">Fahrenheit (°F)</option>
              <option value="kelvin">Kelvin (K)</option>
            </select></td>
          </tr>
        </tbody>
      </table>
      <div class="output-group">
        <hr>
        <p class="resultado">{{ resultado }}</p>
      </div>
      <button @click="regresar" class="regresar-btn">Regresar</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: null,
      unidadOrigen: 'celsius',
      unidadDestino: 'celsius',
      resultado: null
    };
  },
  methods: {
    convertir() {
      const unidades = {
        celsius: {
          celsius: valor => valor,
          fahrenheit: valor => (valor * 9/5) + 32,
          kelvin: valor => valor + 273.15
        },
        fahrenheit: {
          celsius: valor => (valor - 32) * 5/9,
          fahrenheit: valor => valor,
          kelvin: valor => (valor + 459.67) * 5/9
        },
        kelvin: {
          celsius: valor => valor - 273.15,
          fahrenheit: valor => (valor * 9/5) - 459.67,
          kelvin: valor => valor
        }
      };

      const valor = parseFloat(this.inputValue);
      const conversion = unidades[this.unidadOrigen][this.unidadDestino];

      if (!isNaN(valor) && conversion) {
        this.resultado = conversion(valor).toFixed(2) + ' ' + this.unidadDestino.toUpperCase();
      } else {
        this.resultado = 'Entrada inválida';
      }
    },
    regresar() {
      this.$router.push('/');
    }
  }
};
</script>

<style scoped>
/* Estilos */
.conversion-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.conversion-box {
  max-width: 400px;
  padding: 20px;
  border: 3px solid black;
  border-radius: 10px;
}

.input-table {
  width: 100%;
}

.input-label {
  text-align: right;
  padding-right: 10px;
}

.input-field,
.select-box {
  width: calc(100% - 100px); /* Establece el ancho */
}

.output-group {
  text-align: center;
}

.resultado {
  font-size: 24px;
  color: red;
}

.regresar-btn {
  display: block;
  margin: 20px auto 0;
  padding: 10px 20px;
  background-color: #333;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  text-align: center;
}
</style>
