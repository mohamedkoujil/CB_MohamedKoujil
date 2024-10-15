<script setup>
import { ref, reactive } from 'vue'
const num = ref(0)
const usuari = reactive({
  nom: 'Calamardo',
  edat: 20
})
const incrementar = () => {
  num.value++
}

const incrementarEdat = () => {
  usuari.edat++
}

const imgSrc =
  'https://www.educaciontrespuntocero.com/wp-content/uploads/2020/04/mejores-bancos-de-imagenes-gratis.jpg'

const title = ref('')

const arrayProductos = ref([
  { id: 1, nom: 'Producte 1' },
  { id: 2, nom: 'Producte 2' },
  { id: 3, nom: 'Producte 3' }
])

const logat = ref(false)
const mostrar = ref(true)
</script>

<template>
  <div class="container">
    <!-- Mostra el valor de num i un botó per incrementar-lo -->
    <h2>Comptador: {{ num }}</h2>
    <button @click="incrementar">Incrementar</button>

    <!-- Mostra el nom de l'usuari i permet canviar-lo -->
    <h2>Exemple reactiu</h2>
    <p>{{ usuari }}</p>
    <button @click="incrementarEdat">Canviar usuari</button>

    <!-- Mostra una imatge amb esdeveniments de ratolí -->
    <h2>Imatge</h2>
    <img
      @mouseenter="console.log('Entra img')"
      @mouseleave="console.log('Surt img')"
      class="img-fluid"
      :src="imgSrc"
      alt="Imatge"
    />

    <!-- Enllaç bidireccional del text amb v-model -->
    <h2>V-Model</h2>
    <p>{{ title }}</p>
    <input type="text" v-model="title" placeholder="a placeholder" />

    <!-- Llista els productes de l'array -->
    <h2>Array</h2>
    <ul>
      <li v-for="producte in arrayProductos" :key="producte.id">{{ producte.nom }}</li>
    </ul>

    <!-- Mostra missatge segons si l'usuari està logat -->
    <h2>Mostrar segons logat</h2>
    <p v-if="logat">Benvingut {{ usuari.nom }}</p>
    <p v-else>No logat</p>

    <!-- Controla la visibilitat del div amb v-show -->
    <h2>Mostrar div o no (-vshow)</h2>
    <div v-show="mostrar">Mostrant div</div>
    <button @click="mostrar = !mostrar">Mostrar</button>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(240, 214, 176);
  padding: 1em;
  border-radius: 0.5em;
  width: 75%;
}

.container img {
  width: 50%;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
