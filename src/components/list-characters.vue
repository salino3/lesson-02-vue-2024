<template>
    <div class="rootList">
        <ul>
            <li v-for="character in characters" :key="character.id" >{{ character.name }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        characters: Array
    }
}
</script>


<style>
@import url('./styles-components.css');

</style>
