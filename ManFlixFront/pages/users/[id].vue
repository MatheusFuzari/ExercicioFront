<script setup>
    const route = useRoute()
    const {data:userFavs} = await useFetch(`http://127.0.0.1:8000/favoritos/?usuario=${route.params.id}`,{
         key: 'loadFetchs'
    });
    const {data:filmes} = await useFetch("http://127.0.0.1:8000/filmes");
    let movieSelected;
    const sendForm = async () => {
        await useFetch('http://127.0.0.1:8000/favoritos/',{
            method: "POST",
            body: {
                "idFilmeFK":movieSelected,
                "idUsuarioFK":parseInt(route.params.id)
            },
            onResponse(){
                alert("Favorito adicionado")
                refreshNuxtData('loadFetchs')
            },
            onResponseError(){
                alert("Erro ao adicionar favorito")
            }
        })
    };
</script>
<template>
    <div>
        <p>You're in users page</p>
        <br>
        <div v-for="(favs, index) in userFavs" :key="index">
            <p>{{ favs.idFilmeFK.nome }}</p><br>
            <img :src="`http://127.0.0.1:8000${favs.idFilmeFK.foto}`">
        </div>
        <br><hr>
        <h3>Adicione um novo filme aos seus favoritos!!</h3>
        <section>
            <select v-model="movieSelected">
                <option v-for="filme in filmes" :key="filme.id" 
                :value="filme.id">{{ filme.nome }}</option>
            </select>
            <br>
            <button @click="sendForm">Adiconar!</button>
        </section>
    </div>
</template>