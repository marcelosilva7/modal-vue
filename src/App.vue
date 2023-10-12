<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

import Modal from './components/Modal.vue'
import { ref, triggerRef } from 'vue';


//aqui a variavel responsavel por guardar se exibe o modal ou nao
const modalTriggers = ref<{ [key: string]: boolean }>({
  buttonTriggers: false
});

//variavel que usa um evento para mudar o estado de exibir do modal
const toggleModal = (trigger: keyof typeof modalTriggers.value) => {
  modalTriggers.value[trigger] = !modalTriggers.value[trigger];
  console.log(modalTriggers.value)
};

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
  <main>
    <h1>Vue Popups</h1>
  <!-- botao chamando a varivel para trocar o estado dela e exibir o modal-->
    <button @click="() => toggleModal('buttonTriggers')">Abrir o Modal</button>
<!-- aqui a condicional se a variavel do modal for true ele aparece se nao ele some junto com o evento relacionado ao botao-->
    <Modal v-if="modalTriggers.buttonTriggers" :toggleModal="() => toggleModal('buttonTriggers')" >
      <h2>Meu modal</h2>
    </Modal>

  </main>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
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

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
