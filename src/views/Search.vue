
<template>
  <div class="wrapper">
    <div class="search">
      <label for="name">Search</label>
      <input name="search" id="search" v-model="searchValue" v-on:input="handleInput" />
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{ item.data[0].description }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Search',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
.wrapper{
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  padding: 30px;
  margin: 0;
   }
  .search{
    display: flex;
    flex-direction:column;
    width: 300px;
  }
  label{
    font-family: Montserrot, sans-serif;
  }
  input{
    height: 30px;
    border: 0;
    border-bottom: 1px solid black;
  }


</style>
