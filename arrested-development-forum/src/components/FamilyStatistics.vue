<script>
export default {
    props: {
        characters: {
            type: Array,
            required: true
        }
    },
    computed: {
        familyStatistics() {
        const families = ['Bluth', 'Fünke', 'Veal']

        const statistics = {
            Bluth: 0,
            Fünke: 0,
            Veal: 0
        };

        this.characters.forEach((character) => {
            families.forEach(family => {
            if (character.family.indexOf(family) > -1) {
                statistics[family] += 1
            }
            })
        })

        return statistics

        // return this.characterList.filter
        // (character => 
        //   character.family.includes('Bluth')
        // )
        // return this.characterList.filter(character => {
        //   if (character.family.contains('Bluth')){
        //     return true
        //   }
        // }).length
        }
    },
}
</script>

<template>
    <h2>{{ message }}</h2>
    <h3>Statistics:</h3>
        <ul>
            <li v-for="(stat, type) in familyStatistics" :key="`character-${stat}-${type}`">{{ type }}: {{ stat }}</li>
        </ul>
        <ul>
            {{ familyStatistics }}
        </ul> 
        
</template>