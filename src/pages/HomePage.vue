<template>
  <main class="pagina">
    <section id="inicio" class="seccion presentacion" aria-labelledby="titulo-inicio">
      <div class="contenido">
        <h1 id="titulo-inicio">El cine empieza aquí</h1>
        <p class="descripcion">Un lugar para descubrir historias y elegir tu próxima película.</p>
      </div>
    </section>

    <section id="peliculas" class="seccion" aria-labelledby="titulo-peliculas">
      <div class="contenido">
        <h2 id="titulo-peliculas">Películas para descubrir</h2>
      </div>
    </section>

    <section id="beneficios" class="seccion" aria-labelledby="titulo-beneficios">
      <div class="contenido">
        <h2 id="titulo-beneficios">Cada visita tiene algo especial</h2>
      </div>
    </section>

    <section id="despedida" class="seccion" aria-labelledby="titulo-despedida">
      <div class="contenido">
        <h2 id="titulo-despedida">La próxima historia te espera</h2>
      </div>
    </section>
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

.descripcion {
  max-width: 38rem;
  margin: 1.5rem 0 0;
  color: #bdbdbd;
  font-size: 1.1rem;
  line-height: 1.6;
}
</style>
