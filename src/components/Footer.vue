<template>
  <footer class="pie-pagina">
    <div class="contenido">
      <p class="marca">Cine<span>Mundo</span></p>
      <p class="mensaje">Nos vemos en la próxima función.</p>
    </div>
  </footer>
</template>

<style scoped>
.pie-pagina {
  background: #111111;
  color: #ffffff;
}

.contenido {
  width: min(100% - 2rem, 1200px);
  min-height: 6rem;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 0.5rem 2rem;
  padding: 1.5rem 0;
}

.marca,
.mensaje {
  margin: 0;
}

.marca {
  font-size: 1.1rem;
  font-weight: 700;
}

.marca span {
  color: #d32f2f;
}

.mensaje {
  color: #bdbdbd;
  font-size: 0.9rem;
}
</style>
