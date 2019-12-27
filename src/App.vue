<template>
   <div class="wrapper">
    <Claim />
    <SearchInput /></div>
</template>
<script>

import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'App',
  components: { Claim, SearchInput },
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
<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800&display=swap');*{box-sizing: border-box;}
body {
font-family: 'Montserrat', sans-serif; margin: 0; padding: 0;}

.wrapper{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  padding: 30px;
  margin: 0;
  background-image: url('./assets/heroimage.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0%;
   }
</style>
