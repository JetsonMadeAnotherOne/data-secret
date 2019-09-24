<template>
  <div class="header">
    <div class="side">
      <router-link to="/data-sources"><img alt="Vue logo" src="../assets/logo.svg"></router-link>
    </div>
    <div class="side">
      <input type="search" placeholder="Search">
      <div class="bell">
        <img alt="bell" src="../assets/bell.png">
      </div>
      <img alt="user" src="../assets/user.png" class="round">
      <div class="menu" v-on:click='showModal'>
        <span class="username">Joe S Gardner</span>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: 'HeaderComponent',
        data: () => ({
            isShowDropdown: false,
        }),
        methods: {
            showModal() {
                console.log(this.isShowDropdown);
                this.isShowDropdown = true
                console.log(this.isShowDropdown);
            },
        },
    }
</script>

<style scoped lang="less">
  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 80px;
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    background: #FFFFFF;

    .side {
      display: flex;
      align-items: center;
      position: relative;
      /*&:before {
        content: url(./../assets/img/icons/search_icon.png);
      }*/
    }


    .bell {
      margin-right: 5%;
      position: relative;
      &:before {
        content: "";
        width: 6px;
        height: 6px;
        background: darkorange;
        -moz-border-radius: 50px;
        -webkit-border-radius: 50px;
        border-radius: 50px;
        position: absolute;
        left: 61.77%;
        right: 29.52%;
        top: 6.16%;
        bottom: 59.69%;
      }
    }

    .username {
      white-space: nowrap;
      color: #220033;
      font-family: Poppins;
      font-style: normal;
      font-weight: 600;
      font-size: 14px;
      line-height: 25px;

    }
    .username::after {
      content: url(./../assets/img/icons/vector.png);
    }
    .round {
      border-radius: 100px;
      margin-right: 5%;
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
      position: relative;
      background: #F0F1F7;
      background-image: url(./../assets/img/icons/search_icon.png);
      background-repeat: no-repeat; /*Убираем повтор изображения*/
      background-position: 4px; /*Позиционируем*/
      outline: none; /*убираем стандартную обводку браузера*/
      -moz-border-radius: 5px; /*закругляем углы для Mozilla*/
      -webkit-border-radius: 5px; /*закругляем углы для Chrome, Safari*/
      border-radius: 7px; /*закругляем углы для остальных браузеров*/
      padding-left: 20px; /*отступ слева от ввода, чтобы текст не был на картинке(выбирать по размеру картинки)*/
      height: 40px; /*высота строки ввода*/
      margin-right: 5%;

    }

  }
</style>
