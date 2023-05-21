<script>
    export default {
        props: {
            character: {
                type: Object,
                required: true,
            },
        },
        emits: ['favorite'],
        methods: {
            favoriteCharacter() {
                this.$emit('favorite', this.character);
            },
        },
    };
</script>


<template>
    <div>
        <p>{{ character.name }}</p>
        <button @click="favoriteCharacter">🔥 Favorite</button>
    </div>
</template>