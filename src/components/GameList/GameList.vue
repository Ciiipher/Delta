<script setup>
  import gameData from '@/data/games.json'
  import { ref, computed } from 'vue';
  import GameEntry from '@/components/GameList/GameEntry.vue'

  const games = ref(gameData);
  const searchTerm = ref('');
  const showError = ref(false);
  const filteredGames = computed(() => {
    if (!searchTerm.value) {
      return games.value;
    }
    
    const adjustedSearch = searchTerm.value.toLowerCase().replace(/\s/g, '');

    const adjustedGamesList = Object.values(games.value).filter((game) =>
      game.title.toLowerCase().replace(/\s/g, '').includes(adjustedSearch)
    );

    showError.value = adjustedGamesList.length === 0;

    return adjustedGamesList;
    
  });

</script>

<template>  
    <div id="search" class="flex flex-shrink-0 mr-4 items-center">
        <input id="searchInput" autocomplete="off" v-model="searchTerm" type="text" placeholder="Search Here">
    </div>

    <div id="gameList">
        <div v-for="game in filteredGames" :key="game.id" class="gameEntryContainer" >
          <GameEntry :game="game" />
        </div>
    </div>

    <div v-if="showError" class="error">
      <p>No games match that criteria. Please try again.</p>
    </div>

    
</template>