<script setup>
import logo from '@/assets/img/logo.png';
import { RouterLink } from 'vue-router';
</script>

<template>
    <nav id="navbar">
        <RouterLink to="/">
            <img :src="logo" />
        </RouterLink>
    </nav>
</template>