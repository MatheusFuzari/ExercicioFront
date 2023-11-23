<script setup>
    const {data:planos} = await useFetch('http://127.0.0.1:8000/assinatura/')
</script>
<template>
    <div>
        <div v-for="plano in planos" :key="plano.id">
            <h2>{{ plano.nome }} -> R$ {{plano.valor}}</h2>
        </div>
    </div>
</template>
