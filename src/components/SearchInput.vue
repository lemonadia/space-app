<template>
<div class="searchWrapper">
        <input name="search" id="search" v-model="searchValue" v-on:input="handleInput" />
</div>
</template>
<script>
export default {
  name: 'SearchInput',
};
</script>
<style>
  .searchWrapper{
    margin-top: 50px;
    display: flex;
    flex-direction:column;
    width: 300px;
  }
  input{
    height: 30px;
    border: 0;
    border-bottom: 1px solid white;
    background: none;
    }
</style>
