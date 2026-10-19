<script setup lang="ts">
import { ref } from 'vue'
import MensajesConfianza from '../components/MensajesConfianza.vue'
import ModalPelicula from '../components/ModalPelicula.vue'
import TarjetaPelicula from '../components/TarjetaPelicula.vue'
import VideoPrincipal from '../components/VideoPrincipal.vue'

const portadasCartelera = import.meta.glob<string>([
  '../assets/cartelera/cartelera*.png',
  '../assets/cartelera/cartelera*.jpg',
  '../assets/cartelera/cartelera*.jfif',
], {
  eager: true,
  query: '?url',
  import: 'default',
})

const datosPeliculas = [
  { titulo: 'Street Fighter', descripcion: 'Acción para los amantes de los combates.' },
  { titulo: 'Halloween', descripcion: 'Una noche de terror en la pantalla grande.' },
  { titulo: 'La odisea', descripcion: 'Un viaje épico lleno de desafíos.' },
  { titulo: 'Origen', descripcion: 'Una aventura entre los sueños y la realidad.' },
  { titulo: 'La Patrulla Canina', descripcion: 'Una aventura para disfrutar en familia.' },
  { titulo: 'Los colores del tiempo', descripcion: 'Una historia que nos lleva a otra época.' },
]

type Pelicula = { titulo: string; descripcion: string; portada: string }

const peliculas: Pelicula[] = []
const peliculaSeleccionada = ref<Pelicula | null>(null)

for (let numero = 1; numero <= 43; numero++) {
  const ruta = `../assets/cartelera/cartelera${numero}`
  const portada =
    portadasCartelera[`${ruta}.png`] ??
    portadasCartelera[`${ruta}.jpg`] ??
    portadasCartelera[`${ruta}.jfif`]

  if (portada) {
    const datos = datosPeliculas[numero - 1]
    peliculas.push({
      titulo: datos?.titulo ?? `Película ${numero}`,
      descripcion: datos?.descripcion ?? 'Una historia para descubrir en CineMundo.',
      portada,
    })
  }
}
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
            :key="pelicula.titulo"
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
