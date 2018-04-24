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
        <tr v-for="(animal, key) in animals" :key="key">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.birth }}</td>
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
        {species: 'cat', name: 'Mike', birth: '2018-03-01'},
        {species: 'dog', name: 'Janny', birth: '2018-01-01'}
      ]
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
