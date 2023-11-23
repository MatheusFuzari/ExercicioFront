<script setup>
    const {data:users} = await useFetch('http://127.0.0.1:8000/usuarios/');
</script>
<template>
    <div>
        <p>You're in users page</p>
        <br>
        <div v-for="(user, index) in users" :key="index">
            <p>{{ user.nome }} --> {{ user.email }}</p><br>
            <nuxt-link :to="`users/${user.id}`"><img :src="`http://127.0.0.1:8000${user.foto}`" /></nuxt-link>
        </div>
    </div>
</template>