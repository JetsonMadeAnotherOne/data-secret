<template>
  <div class="section">
    <div class="header">
      <div class="container">
        <div class="row">
          <router-link to="/data-secrets"><img alt="Vue logo" src="../assets/images/logo.svg" class="logo">
          </router-link>
          <div class="side">
            <input type="search" placeholder="Search">
            <div class="bell">
              <div class="red-dot"></div>
              <img alt="bell" src="../assets/images/bell.png">
            </div>
            <img alt="user" src="../assets/images/user.png" class="round">
            <div class="menu">
              <div id="demo">
                <div class="modal-db" v-show="showDropdown">
                  <div class="modal-container">
                    <h1>Paragraph #1</h1>
                    <h1>Paragraph #2</h1>
                  </div>
                </div>
                <div @mouseover="mouseOver" @mouseleave="showDropdown = false" class="username">Joe S Gardner</div>
              </div>
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
            showDropdown: false,
        }),
        methods: {
            mouseOver: function () {
                this.showDropdown = !this.showDropdown;
            }
        },
    }
</script>

<style scoped lang="less">

  .header {
    position: relative;
    height: 80px;
    width: 100%;
    left: 0;
    right: 0;
    justify-content: space-between;
    display: block;
    align-items: center;
    background: #FFFFFF;
    box-shadow: 0px 4px 15px rgba(189, 196, 224, 0.192);

    &:before, &:after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      width: 9999px;
      background: #FFFFFF;
      box-shadow: 0px 4px 15px rgba(189, 196, 224, 0.192);
    }

    &:before {
      right: 100%;
    }

    &:after {
      left: 100%;
    }

    .logo {
      position: relative;
      right: 17px;
    }

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
      padding-right: 12px;
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
      background-position: 4px;
    }

    .modal-db {
      margin-top: 23%;
      margin-left: 25%;
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(247, 248, 252, 0.7);
      backdrop-filter: blur(6px);

      .modal-container {
        position: relative;
        padding: 40px;
        width: 276px;
        height: 190px;
        background-color: lightgrey;
        box-shadow: 0px 4px 15px rgba(189, 196, 224, 0.192);
        border-radius: 8px;

      }
    }
  }
</style>
