<script setup lang="ts">
import { onErrorCaptured, ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})

// eslint-disable-next-line @typescript-eslint/no-unused-vars
const menuIsopen = ref(false)
</script>

<template>
  <header>
    <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
    <nav id="mainNav">
      <ul>
        <li><RouterLink to="/" class="text-red-300 underline"> Accueil </RouterLink></li>
        <li><RouterLink to="/accordeon" class="text-red-500 underline"> Accodeon </RouterLink></li>
      </ul>
    </nav>
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
  <button
    aria-controls="mainNav"
    aria-expanded="true"
    class="rounded-full border-2 border-red-600 bg-red-300 px-2"
  >
    menu
  </button>
</template>
