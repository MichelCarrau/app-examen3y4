<template>
  <div id="app">
    <!-- Ejercicio 3 -->
    <h1>Ejercicio 3: Contar vocales en un texto</h1>
    <p>Introduce un texto y haz clic en "Contar" para ver cuántas vocales contiene.</p>
    <input v-model="textoUsuario" type="text" placeholder="Escribe algo aquí" />
    <button @click="contarVocales">Contar</button>
    <div v-if="resultadoVocales !== null" class="resultado">
      El número de vocales es: {{ resultadoVocales }}
    </div>

    <!-- Ejercicio 4 -->
    <h1>Ejercicio 4: Piedra, Papel o Tijera</h1>
    <p>Selecciona tu opción y compite contra la computadora.</p>
    <div class="opciones">
      <button @click="jugar('piedra')">Piedra</button>
      <button @click="jugar('papel')">Papel</button>
      <button @click="jugar('tijera')">Tijera</button>
    </div>
    <div v-if="resultadoJuego" class="resultado">
      <p><strong>Tú elegiste:</strong> {{ opcionUsuario }}</p>
      <p><strong>La computadora eligió:</strong> {{ opcionPC }}</p>
      <p><strong>Resultado:</strong> {{ resultadoJuego }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      // Ejercicio 3
      textoUsuario: "",
      resultadoVocales: null,
      // Ejercicio 4
      opcionUsuario: "",
      opcionPC: "",
      resultadoJuego: "",
    };
  },
  methods: {
    // Ejercicio 3
    contarVocales() {
      const vocales = "aeiouAEIOU";
      let contador = 0;
      for (let caracter of this.textoUsuario) {
        if (vocales.includes(caracter)) {
          contador++;
        }
      }
      this.resultadoVocales = contador;
    },
    // Ejercicio 4
    jugar(opcionUsuario) {
      this.opcionPC = this.generarOpcionPC();
      if (opcionUsuario === this.opcionPC) {
        this.resultadoJuego = "Empate ";
      } else if (
        (opcionUsuario === "piedra" && this.opcionPC === "tijera") ||
        (opcionUsuario === "papel" && this.opcionPC === "piedra") ||
        (opcionUsuario === "tijera" && this.opcionPC === "papel")
      ) {
        this.resultadoJuego = "¡Ganaste! ";
      } else {
        this.resultadoJuego = "Perdiste";
      }
    },
    generarOpcionPC() {
      const opciones = ["piedra", "papel", "tijera"];
      const indiceAleatorio = Math.floor(Math.random() * opciones.length);
      return opciones[indiceAleatorio];
    },
  
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
  color: #333;
}

input {
  font-size: 16px;
  border: 1px solid #ccc;
}

button {
  font-size: 16px;
  background-color: #d454ae;
  color: white;
  cursor: pointer;
  border: none;
}


.opciones button {
  margin: 10px;
}
</style>
