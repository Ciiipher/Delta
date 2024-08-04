<script setup>
    import { ref, computed } from 'vue';
    import { useRoute, useRouter } from 'vue-router';
    import gameData from '@/data/games.json'
  
    const route = useRoute();
    const router = useRouter();
    const games = ref(gameData);
  
    const selectedGame = computed(() => {
        const gameId = route.params.id;
        return Object.values(games.value).find(game => game.game_id === gameId);
    });

    const adjustedDescription = computed(() => {
        return selectedGame.value.content
    .replace(/<\/?p>/gi, '')  // Remove <p> and </p> tags
    .replace(/<br\s*\/?>/gi, ''); // Remove <br> and <br /> tags
    });
  
    // Navigate back to game list
    const goBack = () => {
      router.push('/'); // Assuming '/' is the route for the game list
    };
</script>

<template>
    <div id="gameLanding" :style="{ 'background-image': 'url(' + selectedGame.game_background + ')' }">
        <h1 id="title">{{ selectedGame.title }} </h1>
    </div>

    <div id="gameDescription">
        <div id="gameDescription__text">{{ adjustedDescription }}</div>
        <img id="gameDescription__image" :style="{ 'background-image': 'url(' + selectedGame.game_background + ')' }" />
    </div>
    
    <div id="gameLogin">
        <a id="gameLogin__link" :href="selectedGame.url">Play Now</a>
    </div>

</template>