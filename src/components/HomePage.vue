<template>
  <div class="container">
    <h1>Bienvenido a la Aplicación de Conversiones</h1>
    <button class="button" @click="irADistancia">Conversiones de Distancia</button>
    <button class="button" @click="irATemperatura">Conversiones de Temperatura</button>
    <button class="button" @click="irAPeso">Conversiones de Peso</button>
  </div>

  <!-- Pie de página -->
  <footer>
    <div class="left">Programación Web</div>
    <div class="center">Tarea 4 Conversiones Vue.js</div>
    <div class="right">Juan Carlos Marín Cascante <br class="mobile-break">@2024</div>
  </footer>
</template>

<script>
export default {
  methods: {
    irADistancia() {
      this.$router.push('/distancia');
    },
    irATemperatura() {
      this.$router.push('/temperatura');
    },
    irAPeso() {
      this.$router.push('/peso');
    }
  }
}
</script>

<style scoped>
/* Importa los estilos de Skeleton CSS */
@import '../css/normalize.css';
@import '../css/skeleton.css';


/* Estilos personalizados */
.container {
  margin: 0 auto; /* Centra el contenedor horizontalmente */
  max-width: 960px; /* Limita el ancho del contenedor */
  padding: 2rem; /* Agrega un relleno interno */
  text-align: center; /* Centra el texto dentro del contenedor */
}

/* Estilos para el pie de página */
footer {
  position: fixed; /* Fijar al final de la pantalla */
  bottom: 0; /* Fijar al borde inferior de la pantalla */
  width: 100%; /* Ancho completo */
  background-color: #413f3f; /* Color de fondo gris claro */
  padding: 1rem; /* Espaciado interno */
  box-shadow: 0 -5px 5px rgba(0, 0, 0, 0.1); /* Sombra */
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.left, .center, .right {
  color: white; /* Letras blancas */
}

.left {
  text-align: left;
}

.center {
  text-align: center;
}

.right {
  text-align: right;
}

/* Estilos para el salto de línea en dispositivos móviles */
.mobile-break {
  display: none; /* Oculta el salto de línea en pantallas grandes */
}

@media (max-width: 600px) {
  .right {
    display: block; /* Muestra el salto de línea en dispositivos móviles */
  }

  .mobile-break {
    display: block; /* Muestra el salto de línea en dispositivos móviles */
  }
}
</style>
