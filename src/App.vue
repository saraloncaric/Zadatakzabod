<script setup>
  import { ref } from 'vue';

  const filmovi = [
    {
      naslov: "The Maze Runner",
      slika: "https://cdn.europosters.eu/image/1300/posteri/the-maze-runner-one-sheet-i23758.jpg"
    },
    {
      naslov: "The Maze Runner: Scorch Trials",
      slika: "https://cdn.europosters.eu/image/750/posters/maze-runner-2-one-sheet-i26613.jpg"
    },
    {
      naslov: "The Maze Runner: Death Cure",
      slika: "https://lumiere-a.akamaihd.net/v1/images/mazerunnerdeathcure_feature-poster_584x800_62521e27.jpeg"
    }
  ];

  const is_dark_mode = ref(true);

  const pozadina = () => {
    is_dark_mode.value = !is_dark_mode.value;
  };

</script>

<template>
  <div class="min-h-screen flex flex-col items-center justify-center p-4 transition-colors duration-300"
    :class="{'bg-gray-900 text-white': is_dark_mode, 'bg-white text-gray-900': !is_dark_mode}">

    <button @click="pozadina" class="fixed top-4 right-4 bg-gray-800 text-white p-2 rounded-full shadow-lg">
      Svijetli/tamni način
    </button>

    <div class="p-6 md:p-8 rounded-2x1 w-full max-w-[1024px] shadow-2xl transition-all duration-500"
      :class="{'bg-gradient-to-br from-emerald-950 to-indigo-950': is_dark_mode, 'bg-gradient-to-br from-emerald-300 to-indigo-300': !is_dark_mode}">

      <h1 class="text-3xl md:text-4xl font-bold text-center">Pozdrav, ja sam Sara Lončarić </h1>

      <h2 class="text-md md:text-lg text-left ml-9 mt-4">Moji omiljeni fimovi:</h2>

      <div class="flex flex-wrap justify-center gap-4 md:gap-6 mt-6">
        <div v-for="film in filmovi" :key="film.naslov"
            class="w-[160px] h-[230px] sm:w-[200px] sm:h-[280px] md:w-[280px] md:h-[400px] 
                overflow-hidden rounded-lg shadow-lg transition-transform duration-300 hover:scale-105 relative">
          
          <img :src="film.slika" :alt="film.naslov" class="w-full h-full object-cover">

        </div>
      </div>

      <div class="flex flex-wrap justify-evenly gap-4 md:gap-4 mt-4 text-sm md:text-lg">
        <span v-for="film in filmovi" :key="film.naslov" class="text-xl">{{ film.naslov }}</span>
      </div>
    
    </div>

  </div>
</template>

<style scoped>
</style>


