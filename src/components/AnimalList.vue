<template>
  <div>
    <h1>Animals</h1>

    <table>
      <thead>
        <th>Name</th>
        <th>Species</th>
        <th>Birthday</th>
        <th>&nbsp;</th>
      </thead>
      <tbody>
        <tr v-for="(animal, key) in animals" :key="key">
          <td>{{ animal.name }}</td>
          <td>{{ animal.species}}</td>
          <td>{{ animal.birthday ? animal.birthday : 'Unknown' }}</td>
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
        { name: "John", species: "species 1", birthday: "01.01.2000."},
        { name: "Jack", species: "species 2", birthday: "02.02.2001."},
        { name: "Mick", species: "species 3", birthday: "03.03.2002,"},
        { name: "Tack", species: "species 4", birthday: ""},
        { name: "Toe", species: "species 5", birthday: ""}
      ],
      newAnimal: {
        name: '',
        species: '',
        birthday: ''
      }
    }
  }
}
</script>

<style>

</style>
