<script setup>
    import { RouterLink } from 'vue-router';

    defineProps({
        game: {
            type: Object,
            default: {},
        }
    })
</script>

<template>
    <RouterLink :to="'/game/' + game.game_id" v-if="game" :game="game" class="gameEntry" :style="{ 'background-image': 'url(' + game.game_background + ')' }">
        <p class="gameEntry__title">{{ game.title }}</p>
    </RouterLink>
</template>