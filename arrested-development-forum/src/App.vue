<script>
export default {
  data() {
    return {
      count: 10,
      counterTitle: 'Counter Standard',
      incrementAmount: 3,
      message: 'Hello it works',
      listOfNumbers: [
        {
          name: 1,
          id: '6a887cd2-f0bf-4321-b192-92016f82a883',
          list: [1, 2, 3]
        },
        {
          name: 2,
          id: '8d14d90b-2d47-473e-8293-d5c324111d0d',
          list: [1, 2, 3]
        },
        {
          name: 3,
          id: 'cd806d65-2309-4625-9104-dcd636cd79b5',
          list: [1, 2, 3]
        },
        {
          name: 4,
          id: '00c939cd-fbf4-46d0-8e61-0bc2ce8a5332',
          list: [1, 2, 3]
        },
        {
          name: 5,
          id: '295a8170-59c1-4462-9de1-3c9cd41cedab',
          list: [1, 2, 3]
        }
      ]
    }
  },
  computed: {
    displayTitle() {
      if (this.count > 20) {
        return 'Counter Standard - Very Long'
      } else {
        return 'Counter Standard'
      }
    },
    optimizedIncrementAmount() {
      return this.displayTitle.length * this.incrementAmount
    }
  },
  methods: {
    // changeIncrementAmount(event){
    //   this.incrementAmount = event.target.value
    // },
    incrementCount(newAmount, event) {
      console.log(newAmount)
      console.log(event)
      this.count += this.optimizedIncrementAmount 
    }
  },
  watch: {
    count(newValue) {
      // console.log(newValue)
      if (newValue > 20) {
        this.counterTitle += ' Very Long'
      }
    }
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

  <h3>Characters:</h3>
  <p v-if="characterList.length === 0">There are no characters</p>
  <ul v-else-if="characterList.length % 2 === 0">
    <li v-for="(character, index) in characterList" :key="`even-character-${index}`">
      <p>{{ character.name }}</p>
      <button @click="favoriteCharacter(character)">🔥 Favorite</button>
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
