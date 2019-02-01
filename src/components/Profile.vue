<template>
<div>
    <p>This is my profile</p>
    <p>My name is {{ name }}</p>
    <p>I am a  {{ profession }}</p>

    <input type="text" v-model="name">
    <input type="text" v-model="profession">
</div>
</template>

<script>
export default {
    name: "Profile",
    data () {
        return { name: "Eddie", profession: "actor" }
    }
   
}
</script>