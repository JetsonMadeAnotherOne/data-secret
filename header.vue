<template>
  <div class="header">
    <div class="side">
      <router-link to="/data-sources"><img alt="Vue logo" src="../assets/logo.svg"></router-link>
    </div>
    <div class="side">
      <input type="text" name="">
      <img alt="bell" src="../assets/bell.png">
      <img alt="user" src="../assets/user.png">
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HeaderComponent',
    props: {}
  }
</script>

<style scoped lang="less">
  .header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 80px;
    border-bottom: 1px solid black;
    .side{
      display: flex;
      align-items: center;
    }
    input {
      font-size: 16px;
      padding: 10px;
      display: block;
      width: 300px;
      border: none;
      border-bottom: 1px solid #ccc;
      border-inline-color: orangered;
      border: 3px solid orange;
      box-shadow: 1px 1px 2px 0 darkorange;
      margin-right: 5%;
    }

    input:focus {
      border: 3px solid deepskyblue;
      box-shadow: 1px 1px 2px 0 aqua;
    }
  }
</style>
