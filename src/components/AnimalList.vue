<template>
  <div>
    <form @submit.prevent="addAnimal">
      <label for="species"></label>
      <input v-model="newAnimal.species" type="text" placeholder="Species">
      <label for="name"></label>
      <input v-model="newAnimal.name" type="text" placeholder="Name">
      <label for="birth"></label>
      <input v-model="newAnimal.birth" type="text" placeholder="Birth">
      <button>Add animal</button>
    </form>
    <table>
      <thead>
        <th>Animal species</th>
        <th>Animal name</th>
        <th>Animal b-day</th>
        <th>&nbsp;</th>
      </thead>
      <tbody>
        <tr v-for="(animal, key) in animals" :key="key" v-if="animal.birth ? animal.birth : animal.birth='unknown'">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.birth }}</td>
          <td>{{ animal.sector }}</td>
          <td><button @click="removeAnimal(animal)">Remove animal</button></td>
          <td><button @click="moveToTop(animal)">Move animal to top</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
const sectors = [
  {name: 'Sector 1', surface: 'Lorem'},
  {name: 'Sector 2', surface: 'Ipsum'},
  {name: 'Sector 3', surface: 'Dolor'}
]
export default {
  name: 'AnimalList',
  data() {
    return {
      animals: [
        {species: 'lion', name: 'Tom', birth: '2018-01-01', sector: sectors[2].name},
        {species: 'frog', name: 'Jerry', birth: '2018-02-01', sector: sectors[0].name},
        {species: 'butterfly', name: 'Melly', birth: '2017-01-01', sector: sectors[1].name},
        {species: 'cat', name: 'Mike', birth: '', sector: sectors[2].name},
        {species: 'dog', name: 'Janny', birth: '', sector: sectors[0].name}
      ],
      newAnimal: {
        species: '',
        name: '',
        birth: ''
      }
    }
  },
  methods: {
    removeAnimal(animal) {
      this.animals.splice(this.animals.indexOf(animal));
    },
    moveToTop(animal) {
      this.animals.pop(animal);
      this.animals.unshift(animal);
    },
    addAnimal() {
      this.animals.push(this.newAnimal);
      this.newAnimal = {
        species: '',
        name: '',
        birth: ''
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
