<script setup lang="ts">
defineProps<{
  titulo: string
  descripcion: string
  portada: string
}>()
</script>

<template>
  <article class="tarjeta">
    <img :src="portada" :alt="`Portada de ${titulo}`" loading="lazy" width="400" height="600" />
    <div class="informacion">
      <h3>{{ titulo }}</h3>
      <p>{{ descripcion }}</p>
    </div>
  </article>
</template>

<style scoped>
.tarjeta {
  height: 100%;
  border: 1px solid #383838;
  background: #1b1b1b;
}

img {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 2 / 3;
  object-fit: cover;
}

.informacion {
  padding: 1.25rem;
}

h3 {
  margin: 0;
  font-size: 1.25rem;
}

p {
  margin: 0.75rem 0 0;
  color: #bdbdbd;
  line-height: 1.5;
}
</style>
