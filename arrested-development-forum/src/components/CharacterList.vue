<script>
export default {
    data : () => ({
        characterList: [
            {
                name: 'Michael Bluth',
                family: ['Bluth']
            },
            {
                name: 'George Michael Bluth',
                family: ['Bluth']
            },
            {
                name: 'Lindsay Bluth Fünke',
                family: ['Bluth', 'Fünke']
            },
            {
                name: 'Tobias Fünke',
                family: ['Fünke']
            },
            {
                name: 'George Oscar "G.O.B." Bluth II',
                family: ['Bluth']
            },
            {
                name: 'Buster Bluth',
                family: ['Bluth']
            },
            {
                name: 'Maeby Fünke',
                family: ['Fünke']
            },
            {
                name: 'Lucille Bluth',
                family: ['Bluth']
            },
            {
                name: 'George Bluth Sr.',
                family: ['Bluth']
            },
            {
                name: 'Ann Veal',
                family: ['Veal']
            }
        ],
        favoriteList: [],
    }),
    methods: {
          
        favoriteCharacter(character) {
        this.favoriteList.push(character);
        },
    }
};
</script>

<template>
    <h3>Characters:</h3>
    <p v-if="characterList.length === 0">There are no characters</p>
    <ul v-else-if="characterList.length % 2 === 0">
        <li v-for="(character, index) in characterList" :key="`even-character-${index}`">
        <p>{{ character.name }}</p>
        <button @click="favoriteCharacter(character)">🔥 Favorite</button>
        </li>
    </ul>
    <p v-else>There are an odd number of characters</p>
</template>