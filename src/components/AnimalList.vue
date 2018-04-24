<template>
  <div>
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
          <td><button @click="removeAnimal(animal)">Remove animal</button></td>
          <td><button @click="moveToTop(animal)">Move animal to top</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data() {
    return {
      animals: [
        {species: 'lion', name: 'Tom', birth: '2018-01-01'},
        {species: 'frog', name: 'Jerry', birth: '2018-02-01'},
        {species: 'butterfly', name: 'Melly', birth: '2017-01-01'},
        {species: 'cat', name: 'Mike', birth: ''},
        {species: 'dog', name: 'Janny', birth: ''}
      ]
    }
  },
  methods: {
    removeAnimal(animal) {
      this.animals.splice(this.animals.indexOf(animal));
    },
    moveToTop(animal) {
      this.animals.pop(animal);
      this.animals.unshift(animal);
    }
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
