<script setup lang="ts">
import { onMounted, ref } from 'vue'
import MensajesConfianza from '../components/MensajesConfianza.vue'
import ModalPelicula from '../components/ModalPelicula.vue'
import TarjetaPelicula from '../components/TarjetaPelicula.vue'
import VideoPrincipal from '../components/VideoPrincipal.vue'

const apiKey = '68f676c7186e888da81b15bf923a9bdd'

type PeliculaApi = { id: number; title: string; overview: string; poster_path: string | null }
type Pelicula = { id: number; titulo: string; descripcion: string; portada: string }

const peliculas = ref<Pelicula[]>([])
const peliculaSeleccionada = ref<Pelicula | null>(null)

onMounted(async () => {
  const respuesta = await fetch(
    `https://api.themoviedb.org/3/movie/now_playing?api_key=${apiKey}&language=es-ES&page=1`,
  )
  const datos: { results: PeliculaApi[] } = await respuesta.json()

  peliculas.value = datos.results
    .filter((pelicula) => pelicula.poster_path)
    .slice(0, 8)
    .map((pelicula) => ({
      id: pelicula.id,
      titulo: pelicula.title,
      descripcion: pelicula.overview || 'Sin descripción disponible.',
      portada: `https://image.tmdb.org/t/p/w500${pelicula.poster_path}`,
    }))
})
</script>

<template>
  <main class="pagina">
    <section id="inicio" class="seccion presentacion" aria-labelledby="titulo-inicio">
      <div class="contenido">
        <h1 id="titulo-inicio">El cine empieza aquí</h1>
        <VideoPrincipal />
      </div>
    </section>

    <section id="peliculas" class="seccion" aria-labelledby="titulo-peliculas">
      <div class="contenido">
        <h2 id="titulo-peliculas">Películas para descubrir</h2>
        <div class="lista-peliculas">
          <TarjetaPelicula
            v-for="pelicula in peliculas"
            :key="pelicula.id"
            :titulo="pelicula.titulo"
            :descripcion="pelicula.descripcion"
            :portada="pelicula.portada"
            @seleccionar="peliculaSeleccionada = pelicula"
          />
        </div>
      </div>
    </section>

    <MensajesConfianza />

    <ModalPelicula
      v-if="peliculaSeleccionada"
      :titulo="peliculaSeleccionada.titulo"
      :descripcion="peliculaSeleccionada.descripcion"
      :portada="peliculaSeleccionada.portada"
      @cerrar="peliculaSeleccionada = null"
    />
  </main>
</template>

<style scoped>
:global(*) {
  box-sizing: border-box;
}

:global(body) {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.pagina {
  min-height: 100vh;
  background: #111111;
  color: #ffffff;
}

.seccion {
  min-height: 42vh;
  border-bottom: 1px solid #383838;
}

.presentacion {
  min-height: 70vh;
  display: flex;
  align-items: center;
}

.contenido {
  width: min(100% - 2rem, 1200px);
  margin: 0 auto;
  padding: 5rem 0;
}

h1,
h2 {
  max-width: 18ch;
  margin: 0;
  line-height: 1.1;
}

h1 {
  font-size: clamp(2.8rem, 7vw, 5.5rem);
}

h2 {
  font-size: clamp(2rem, 4vw, 3.4rem);
}

.lista-peliculas {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 15rem), 1fr));
  gap: 1.5rem;
  margin-top: 2.5rem;
}
</style>
