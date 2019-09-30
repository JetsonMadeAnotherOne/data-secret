<template>
  <div class="section">
    <div class="header">
      <div class="container">
        <div class="row">
          <router-link to="/data-sources"><img alt="Vue logo" src="../assets/logo.svg" class="logo"></router-link>
          <div class="side">
            <input type="search" placeholder="Search">
            <div class="bell">
              <div class="red-dot"></div>
              <img alt="bell" src="../assets/img/icons/bell.png">
            </div>
            <img alt="user" src="../assets/user.png" class="round">
            <div class="menu">
              <div class="username" v-on:click='showModal'>Joe S Gardner</div>
            </div>
          </div>
        </div>
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
    .logo {
      position: relative;
      right: 17px;
    }

    &:before, &:after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      width: 9999px;
      background: #FFFFFF;
      box-shadow: 0px 4px rgba(189, 196, 224, 0.192);
    }

    &:before {
      right: 100%;
    }

    &:after {
      left: 100%;
    }

    position: relative;
    height: 80px;
    width: 100%;
    left: 0;
    right: 0;
    justify-content: space-between;
    display: block;
    align-items: center;
    background: #FFFFFF;
    box-shadow: 0px 4px rgba(189, 196, 224, 0.192);

    .row {
      padding-right: 30px;
      padding-left: 30px;
      height: 80px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .side {
      display: flex;
      align-items: center;
      position: relative;
    }


    .bell {
      margin-right: 36.98px;
      position: relative;
    }

    .red-dot {
      content: "";
      width: 6px;
      height: 6px;
      background: darkorange;
      border-radius: 50px;
      position: absolute;
      left: 61.77%;
      right: 90.52%;
      top: 6.16%;
      bottom: 59.69%;
      box-shadow: -1.5px 2px 7px 0.2px orange;
    }


    .username {
      position: relative;
      font-family: Poppins;
      font-style: normal;
      font-weight: 600;
      font-size: 14px;
      line-height: 25px;
      white-space: nowrap;
      color: #220033;
      right: -2px;
      cursor: pointer;
    }

    .username::after {
      content: url(./../assets/img/icons/vector.png);
      position: relative;
      right: -16.5px;
      cursor: pointer;
    }

    .round {
      border-radius: 100px;
      margin-right: 15px;
    }

    input {
      outline: none;
      font-family: Poppins;
      font-style: normal;
      font-weight: normal;
      font-size: 14px;
      line-height: 24px;
      padding: 10px;
      height: 40px;
      width: 300px;
      display: flex;
      align-items: center;
      position: relative;
      border-radius: 7px;
      padding-left: 25px;
      margin-right: 42px;
      background: #F0F1F7;
      background-image: url(./../assets/img/icons/search_icon.png);
      background-repeat: no-repeat;
      background-position: 4.25px;
    }


    .section {
      width: 50%;
      margin: 0 auto;
    }
  }
</style>
