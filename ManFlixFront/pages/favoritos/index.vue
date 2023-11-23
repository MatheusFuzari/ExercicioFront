<script setup>
    const {data:userFavs} = await useFetch(`http://127.0.0.1:8000/favoritos`);
</script>
<template>
    <div>
        <p>You're in favs page</p>
        <br>
        <div v-for="(favs, index) in userFavs" :key="index">
            <p>{{ favs.idFilmeFK.nome }}</p><br>
            <img :src="`http://127.0.0.1:8000${favs.idFilmeFK.foto}`">
        </div>
    </div>
</template>