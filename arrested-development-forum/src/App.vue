<script>
import CharacterList from './components/CharacterList.vue'

export default {
  components: {
    CharacterList,
  },
  data: () => ({
    message: 'Arrested Development',
    newCharacter: {
      name: '',
      family: []
    },

    favoriteList: []
  }),
  computed: {
    familyStatistics() {
      const families = ['Bluth', 'Fünke', 'Veal']

      const statistics = {
        Bluth: 0,
        Fünke: 0,
        Veal: 0
      }

      this.characterList.forEach(character => {
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
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = {
        name: ''
      }
    },
  }
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
<!-- Placeholder for CharacterList -->
  <CharacterList />
  <h3>Favorite Characters</h3>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character, index) in favoriteList" :key="`odd-character-${index}`">
      {{ character.name }}
    </li>
  </ul>
  <p v-else>There are no favorite characters!</p>
  <h3>New Character</h3>
  <pre>
    {{ newCharacter }}
  </pre>
  <label for="character-name">Name</label>
  <input type="text" v-model="newCharacter.name"
  @keyup.enter="addNewCharacter" />
</template>
