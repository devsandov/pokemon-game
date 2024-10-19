<template>
  <section
    v-if="isLoading || randomPokemon.id === null"
    class="flex flex-col justify-center items-center w-screen h-screen"
  >
    <h1 class="text-3xl">Wait a minute!</h1>
    <h3 class="animate-pulse">Loading pokemons...</h3>
  </section>

  <section v-else class="flex flex-col justify-center items-center w-screen h-screen">
    <h1 class="m-5">Who is this pokemon?</h1>
    <h2>{{ randomPokemon }}</h2>
    <PokemonPicture
      :pokemon-id="randomPokemon.id"
      :show-pokemon="gameStatus !== GameStatus.Playing"
    />

    <PokemonOptions :options="options" @selected-option="onSelectedOption" />
  </section>
</template>

<script setup lang="ts">
import PokemonOptions from '../components/PokemonOptions.vue';
import PokemonPicture from '../components/PokemonPicture.vue';
import { usePokemonGame } from '../composables/usePokemonGame';
import { GameStatus } from '../interfaces';

const { randomPokemon, gameStatus, pokemonOptions: options, isLoading } = usePokemonGame();
const onSelectedOption = (value: number) => {
  console.log();
};
</script>
