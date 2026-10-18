<script setup lang="ts">
import iconoLogin from '../assets/login.png'
</script>

<template>
  <header class="encabezado">
    <div class="contenido">
      <a class="marca" href="#inicio" aria-label="CineMundo: volver al inicio">
        Cine<span>Mundo</span>
      </a>

      <img class="icono-acceso" :src="iconoLogin" alt="Usuario" width="32" height="32" />
    </div>
  </header>
</template>

<style scoped>
.encabezado {
  border-bottom: 1px solid #383838;
  background: #111111;
  color: #ffffff;
}

.contenido {
  width: min(100% - 2rem, 1200px);
  min-height: 4.5rem;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.5rem;
}

.marca {
  color: inherit;
  font-size: 1.25rem;
  font-weight: 700;
  text-decoration: none;
}

.marca span {
  color: #d32f2f;
}

.icono-acceso {
  display: block;
  width: 32px;
  height: 32px;
}
</style>
