<script setup>
    const {data:filmes} = await useFetch('http://127.0.0.1:8000/filmes/')
</script>
<template>
    <div>
        <div v-for="filme in filmes" :key="filme.id">
            <h2>{{ filme.nome }}</h2>
            <nuxt-link :to="`filmes/${filme.id}`"><img :src="`http://127.0.0.1:8000${filme.banner}`"></nuxt-link>
        </div>
    </div>
</template>
