<template>
  <div class="header">
    <div class="side">
      <router-link to="/data-sources"><img alt="Vue logo" src="../assets/logo.svg"></router-link>
    </div>
    <div class="side">
      <input type="search" placeholder= "Search" name="">

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
      font-family: Poppins;
      font-style: normal;
      font-weight: normal;
      font-size: 14px;
      line-height: 24px;
      padding: 10px;
      display: flex;
      align-items: center;
      width: 300px;
      border-bottom: 1px solid #ccc;
      border-inline-color: orangered;
      border: 3px solid orange;
      box-shadow: 1px 1px 2px 0 darkorange;
      margin-right: 5%;
      background: #F0F1F7;
      border-radius: 7px;
    }

    input:focus {
      border: 3px solid deepskyblue;
      box-shadow: 1px 1px 2px 0 aqua;
    }
  }
</style>
