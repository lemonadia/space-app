
<template>
  <div class="wrapper">
    <div class="search"><label for="name">Search</label>
      <input name="search" /></div>
  </div>
</template>

<script>
export default {
  name: 'Home',
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
