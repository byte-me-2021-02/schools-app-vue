

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p><input type="text" v-model="search"></p>
    <div v-for="school in filterBy(schools, search, 'name')">
      <p>name: {{school.name}}</p>
      <p>dbn: {{school.dbn}}</p>      
      <p>number_of_participants: {{school.number_of_participants}}</p>
      <p>reading: {{school.reading}}</p>
      <p>math: {{school.math}}</p>
      <p>difference: {{school.math - school.reading}}</p>
      <p>writing: {{school.writing}}</p>
      <p>total: {{school.total}}</p>
      <p>rank: {{school.rank}}</p>
      <hr>
    </div>
  </div>
</template>

<style>
</style>

<script>
import Vue2Filters from "vue2-filters";
import axios from "axios";
export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      search: "",
      schools: []
    };
  },
  created: function() {
    axios.get('/api/schools').then(response => {
      this.schools = response.data;
    });
  },
  methods: {}
};
</script>

