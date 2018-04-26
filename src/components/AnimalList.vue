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
          <td>{{ animal.sector }}</td>
          <td>
            <button @click="deleteContact(key)">Remove</button>
          </td>
          <td>
            <button @click="moveAnimalToTop(animal)">Move to top</button>
          </td>
        </tr>
      </tbody>
    </table>

    <form @submit.prevent="addAnimal">
      <label>Name</label>
      <input type="text" v-model="newAnimal.name" placeholder="Name" /><br>
      <label>Species</label>
      <input type="text" v-model="newAnimal.species" placeholder="Species" /><br>
      <label>Birthday</label>
      <input type="text" v-model="newAnimal.birthday" placeholder="Birthday" /><br>
      <button type="submit">Add Animal</button>
    </form>
  </div>
</template>

<script>
const sectors = [
  { name: 'Sector 1', surface: 'surface-1' },
  { name: 'Sector 2', surface: 'surface-2' },
  { name: 'Sector 3', surface: 'surface-3' }
]
export default {
  name: 'AnimalList',
  data() {
    return {
      animals: [
        { name: "John", species: "species 1", birthday: "01.01.2000.", sector: sectors[0].name },
        { name: "Jack", species: "species 2", birthday: "02.02.2001.", sector: sectors[0].name },
        { name: "Mick", species: "species 3", birthday: "03.03.2002.", sector: sectors[1].name },
        { name: "Tack", species: "species 4", birthday: "", sector: sectors[1].name },
        { name: "Toe", species: "species 5", birthday: "", sector: sectors[2].name }
      ],
      newAnimal: {
        name: '',
        species: '',
        birthday: '',
        sector: ''
      }
    }
  },
  methods: {
    deleteContact(key) {
      this.animals.splice(key, 1);
    },
    moveAnimalToTop(animal) {
      this.animals.splice(this.animals.indexOf(animal), 1);
      this.animals.unshift(animal);
    },
    addAnimal() {
      this.newAnimal.sector = sectors[2].name;
      this.animals.push(this.newAnimal);
      this.newAnimal = {};
    }
  }
}
</script>

<style>

</style>
