<script setup>
    const route = useRoute()
    const {data:filmes} = await useFetch(`http://127.0.0.1:8000/filmes/${route.params.id}`);
</script>
<template>
    <div>
        <h2>{{ filmes.nome }}</h2>
        <h3>Gênero: {{ filmes.idCategoriaFK.nome }}</h3>
        <p>{{ filmes.descricao }}</p>
        <img :src="`http://127.0.0.1:8000${filmes.banner}`"><br>
        <img :src="`http://127.0.0.1:8000${filmes.foto}`"><br>
        <img :src="`http://127.0.0.1:8000${filmes.logo}`">
    </div>
</template>
