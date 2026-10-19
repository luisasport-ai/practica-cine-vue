<template>
  <section id="beneficios" class="mensajes" aria-label="Mensajes de confianza">
    <div class="contenido">
      <article class="panel">
        <h2>Cada visita tiene algo especial</h2>
        <p>Encuentra películas para distintos gustos y elige qué ver a tu ritmo.</p>
      </article>

      <article class="panel panel-derecho">
        <h2>La próxima historia te espera</h2>
        <p>Vuelve cuando quieras y descubre una nueva película en nuestra cartelera.</p>
      </article>
    </div>
  </section>
</template>

<style scoped>
.mensajes {
  border-bottom: 1px solid #383838;
  background: #111111;
  color: #ffffff;
}

.contenido {
  width: min(100% - 2rem, 1200px);
  margin: 0 auto;
  padding: 5rem 0;
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.5rem;
}

.panel {
  padding: 2rem;
  border: 1px solid #383838;
  background: #1b1b1b;
}

.panel-derecho {
  text-align: right;
}

h2 {
  max-width: 18ch;
  margin: 0;
  font-size: clamp(1.8rem, 3vw, 2.6rem);
  line-height: 1.1;
}

p {
  max-width: 28rem;
  margin: 1.25rem 0 0;
  color: #bdbdbd;
  line-height: 1.6;
}

.panel-derecho h2,
.panel-derecho p {
  margin-left: auto;
}

@media (max-width: 640px) {
  .contenido {
    grid-template-columns: 1fr;
  }

  .panel-derecho {
    text-align: left;
  }

  .panel-derecho h2,
  .panel-derecho p {
    margin-left: 0;
  }
}
</style>
