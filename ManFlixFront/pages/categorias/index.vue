<script setup>
    const {data:categs} = await useFetch('http://127.0.0.1:8000/categoria/')
</script>
<template>
    <div>
        <div v-for="categ in categs" :key="categ.id">
            <p>{{categ.nome}}</p>
        </div>        
    </div>
</template>
