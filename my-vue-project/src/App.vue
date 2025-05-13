<script setup>
import NavbarComponent from "./components/NavbarComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";
import { ref, computed } from 'vue'

// Iteración 2
const nombre = ref("Ana")
const edad = ref(28)

function saludo() {
  return `Hola, ${nombre.value}. Tienes ${edad.value} años.`
}

const saludoComputado = computed(() => {
  return `Hola, ${nombre.value}. Tienes ${edad.value} años.`
})

// Iteración 3
const mostrarMensaje = ref(true)

// Iteración 4
const publicaciones = ref([
  {
    titulo: "Vue 3 para principiantes",
    descripcion: "Una introducción clara a Vue 3",
    contenido: "Este artículo cubre los fundamentos de Vue 3 incluyendo composición y reactividad."
  },
  {
    titulo: "Reactividad avanzada",
    descripcion: "Cómo funciona internamente el sistema reactivo de Vue",
    contenido: "Aprende a usar refs, reactive, computed y watch para crear interfaces dinámicas."
  },
  {
    titulo: "Guía de componentes",
    descripcion: "Cómo dividir tu app en partes reutilizables",
    contenido: "Explora la creación, reutilización y comunicación entre componentes en Vue."
  }
])

// Iteración 5: Cambiar el color de fondo
const colorFondo = ref("white")

function cambiarColorFondo() {
  // Cambiar el color de fondo al azar
  const colores = ["white", "lightblue", "lightgreen", "lightcoral", "lightyellow"]
  colorFondo.value = colores[Math.floor(Math.random() * colores.length)]
}
</script>

<template>
  <NavbarComponent />

  <div>
    <!-- Iteración 2 -->
    <p>2 + 2 = {{ 2 + 2 }}</p>
    <p>Mensaje (con función): {{ saludo() }}</p>
    <p>Mensaje (con computed): {{ saludoComputado }}</p>

    <!-- Iteración 3 -->
    <p v-if="mostrarMensaje">Este párrafo solo aparece si mostrarMensaje es true.</p>

    <!-- Iteración 4 -->
    <h2>Lista de publicaciones:</h2>
    <ul>
      <li v-for="(post, index) in publicaciones" :key="index">
        <h3>{{ post.titulo }}</h3>
        <p><strong>{{ post.descripcion }}</strong></p>
        <p>{{ post.contenido }}</p>
      </li>
    </ul>

    <!-- Iteración 5: Cambiar color de fondo -->
    <div :style="{ backgroundColor: colorFondo }" class="fondo-cambio">
      <p>Este es un área cuyo color de fondo cambiará al presionar el botón.</p>
      <button @click="cambiarColorFondo">Cambiar color de fondo</button>
    </div>
  </div>

  <FooterComponent />
</template>

<style>
.fondo-cambio {
  padding: 20px;
  margin-top: 20px;
  text-align: center;
}
</style>

