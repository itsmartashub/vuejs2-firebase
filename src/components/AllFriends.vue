<template>
    <div id="all-friends">
        <h2>All Friends</h2>
        <div v-for="(friend, index) in prijatelji" :key="index"> <!-- v-for trazi unikatan :key, za sad cemo staviti da to bude index, bez ovog :key="index" javlja se greska -->
            <span v-on:click="unfriend(friend.name)">{{ friend.name }} </span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AllFriends', 

    props: ['prijatelji'],

    data() {
        return {
        }
    },

    methods: {
        unfriend(name) {
            this.$emit("brisanje", { ime: name })  // da bismo emitovali event iz child u parenta to radimo sa $emit, njemu prosledjujemo dva parametra, prvi je string, tj ime custom emit eventa, koje god, a drugi arg je objekat u kom je argument koji prosledjujemo u f-ji unfriend(). Sada u App.vue u delu gde pozivamo <AllFriends /> pozivamo ovaj custom event
        }
    }
}
</script>

<style>

</style>