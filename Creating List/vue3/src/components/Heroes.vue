<template>
    <ul>
    <li v-for="(h,index) in heroes" :key="h.name">
      <div>{{ h.name }} <button class="danger" v-on:click="remove(index)">x</button></div>
      </li>
  </ul>
  <form @submit.prevent="addHero">
    <input v-model="newHero" placeholder="Type hero name here" />
    <button type="submit">Add Hero</button>
  </form>
</template>

<script>
export default {
    computed:{
    heroCount(){
      return this.heroes.length;
    }
  },
  methods: {
    addHero() {
      if(this.newHero !== ""){
      this.heroes.push({ name: this.newHero });
      this.newHero = "";
      }
    },
    remove(index){
      
      this.heroes=this.heroes.filter((hero,i) => i!==index)
    },
  },
 data() {
    return {
      newHero: "Aquaman",
      heroes: [
        { name: "batman" },
        { name: "spiderman" },
        { name: "superman" },
        { name: "hulk" },
      ],
    };
  },
}
</script>

<style>

</style>