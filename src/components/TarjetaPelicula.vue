<script setup lang="ts">
defineProps<{
  titulo: string
  descripcion: string
  portada: string
}>()

const emitir = defineEmits(['seleccionar'])
</script>

<template>
  <button
    class="tarjeta"
    type="button"
    :aria-label="`Ver detalles de ${titulo}`"
    @click="emitir('seleccionar')"
  >
    <img :src="portada" alt="" loading="lazy" width="400" height="600" />
    <span class="informacion">
      <span class="titulo">{{ titulo }}</span>
      <span class="descripcion">{{ descripcion }}</span>
    </span>
  </button>
</template>

<style scoped>
.tarjeta {
  display: block;
  width: 100%;
  height: 100%;
  padding: 0;
  border: 1px solid #383838;
  background: #1b1b1b;
  color: #ffffff;
  font: inherit;
  text-align: left;
  cursor: pointer;
}

.tarjeta:focus-visible {
  outline: 2px solid #ffffff;
  outline-offset: 2px;
}

img {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 2 / 3;
  object-fit: cover;
}

.informacion {
  display: block;
  padding: 1.25rem;
}

.titulo {
  display: block;
  font-size: 1.25rem;
  font-weight: 700;
}

.descripcion {
  display: block;
  margin-top: 0.75rem;
  color: #bdbdbd;
  line-height: 1.5;
}
</style>
