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
    <h2>Comptador: {{ num }}</h2>
    <button @click="incrementar">Incrementar</button>

    <h2>Exemple reactive</h2>
    <p>{{ usuari }}</p>
    <button @click="incrementarEdat">Canvar usuari</button>

    <h2>Imatge</h2>
    <img
      @mouseenter="console.log('Entra img')"
      @mouseleave="console.log('Surt img')"
      class="img-fluid"
      :src="imgSrc"
      alt="Imatge"
    />

    <h2>V-Model</h2>
    <p>{{ title }}</p>
    <input type="text" v-model="title" placeholder="a placeholder" />

    <h2>Array</h2>
    <ul>
      <li v-for="producte in arrayProductos" :key="producte.id">{{ producte.nom }}</li>
    </ul>

    <p v-if="logat">Benvingut {{ usuari.nom }}</p>
    <p v-else>No logat</p>

    <div v-show="mostrar">Mostrant div</div>
    <button @click="mostrar = !mostrar">Mostrar</button>
  </div>
</template>

<style scoped>
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
