<template>
    <div id="online-friends">
        <h2>Online friends</h2>
        <div v-for="(friend, index) in prijatelji" :key="index">
            <span v-if="friend.online"> {{ friend.name }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'OnlineFriends',
    props: ['prijatelji'],
    data() {
        return {
            
        }
    }
}
</script>


<style>
span {
    cursor: pointer;
}
</style>