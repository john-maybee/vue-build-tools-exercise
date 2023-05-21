<script>
import FamilyStatistics from './components/FamilyStatistics.vue';
import CharacterCard from './components/CharacterCard.vue';

export default {
  components: {
    FamilyStatistics,
    CharacterCard
  },
  
    data: () => ({
      message: 'Arrested Development',
      newCharacter: {
        name: '',
        family: []
      },
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
      favoriteList: []
    }),
    
    methods: {
      addNewCharacter() {
        this.characterList.push(this.newCharacter)
        this.newCharacter = {
          name: ''
        }
      },
      addFavoriteCharacter(payload) {
        this.favoriteList.push(payload);
      }
    }
  }
</script>

<template>
  
  <!-- <ul>
    {{ familyStatistics }}
  </ul> -->
  <FamilyStatistics :characters="characterList"/>
  <h3>Characters:</h3>
  <p v-if="characterList.length === 0">There are no characters</p>
  <ul v-else-if="characterList.length % 2 === 0">
    <li v-for="(character, index) in characterList" :key="`even-character-${index}`">
      <!--Placeholder-->
      <CharacterCard :character="character" @favorite="addFavoriteCharacter" />
    </li>
  </ul>
  <p v-else>There are an odd number of characters</p>
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
