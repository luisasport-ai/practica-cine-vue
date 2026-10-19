<script setup lang="ts">
import { onMounted, ref } from 'vue'

defineProps<{
  titulo: string
  descripcion: string
  portada: string
}>()

const emitir = defineEmits(['cerrar'])
const dialogo = ref<HTMLDialogElement | null>(null)

onMounted(() => dialogo.value?.showModal())

function cerrar() {
  dialogo.value?.close()
}
</script>

<template>
  <dialog ref="dialogo" aria-labelledby="titulo-modal" @close="emitir('cerrar')">
    <div class="detalle">
      <img :src="portada" :alt="`Portada de ${titulo}`" width="400" height="600" />
      <div class="informacion">
        <button type="button" autofocus @click="cerrar">Cerrar</button>
        <h2 id="titulo-modal">{{ titulo }}</h2>
        <p>{{ descripcion }}</p>
      </div>
    </div>
  </dialog>
</template>

<style scoped>
dialog {
  width: min(800px, calc(100% - 2rem));
  max-height: calc(100vh - 2rem);
  overflow: auto;
  padding: 0;
  border: 1px solid #555555;
  background: #1b1b1b;
  color: #ffffff;
}

dialog::backdrop {
  background: rgba(0, 0, 0, 0.8);
}

.detalle {
  display: grid;
  grid-template-columns: minmax(0, 2fr) minmax(0, 3fr);
}

img {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 2 / 3;
  object-fit: cover;
}

.informacion {
  padding: 2rem;
}

button {
  display: block;
  margin-left: auto;
  padding: 0.5rem 0.75rem;
  border: 1px solid #777777;
  background: transparent;
  color: inherit;
  font: inherit;
  cursor: pointer;
}

h2 {
  margin: 2rem 0 0;
  font-size: clamp(1.8rem, 3vw, 2.6rem);
}

p {
  margin: 1rem 0 0;
  color: #bdbdbd;
  line-height: 1.6;
}

@media (max-width: 600px) {
  .detalle {
    grid-template-columns: 1fr;
  }
}
</style>
