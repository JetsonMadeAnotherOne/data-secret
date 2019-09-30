<template>
  <div class="section">
    <div class="header">
      <div class="container">
        <div class="row">
          <div class="sync" >
            <div class="description" v-on:click='showModal("db")'>
              <p>SYNC FROM DB CONNECT</p>
            </div>
            <div class="modal-db" v-if="showModalDB">

              <div class="modal-container">
                <div class="close" @click="showModal('db')"></div>
                <div class="modal-header">
                  <h2>Data base</h2>
                  <slot name="header">
                  </slot>
                </div>

                <div class="modal-body">
                  <slot name="body">

                    <label class="main-label" for="guard-key">Database Type</label>
                    <input
                      class="main-input"
                      type="text"
                      v-model="dbData.dbType"
                      name="guard-key"
                      placeholder="Enter Database Type ">

                    <label class="main-label" for="guard-key">Host</label>
                    <input
                      class="main-input"
                      type="text"
                      v-model="dbData.host"
                      name="guard-key"
                      placeholder="Enter Host ">

                    <label class="main-label" for="guard-key">Database Name</label>
                    <input
                      class="main-input"
                      type="text"
                      v-model="dbData.dbName"
                      name="guard-key"
                      placeholder="EnterDatabase Name">

                    <label class="main-label" for="guard-key">User</label>
                    <input
                      class="main-input"
                      type="text"
                      v-model="dbData.user"
                      name="guard-key"
                      placeholder="Enter User Name ">

                    <label class="main-label" for="guard-key">Password</label>
                    <input
                      class="main-input"
                      type="password"
                      v-model="dbData.password"
                      name="Password"
                      placeholder="Enter Password ">

                  </slot>
                </div>

                <div class="modal-footer">
                  <slot name="footer">
                    <button type="button" class="button-main" @click="sendDbCredential">
                      Connect
                    </button>
                  </slot>
                </div>
              </div>

            </div>
          </div>
          <router-link to="/data-secrets"><img alt="Vue logo" src="../assets/images/logo.svg" class="logo"></router-link>
          <div class="side">
            <input type="search" placeholder="Search">
            <div class="bell">
              <div class="red-dot"></div>
              <img alt="bell" src="../assets/images/bell.png">
            </div>
            <img alt="user" src="../assets/images/user.png" class="round">
            <div class="menu">
              <div class="username" v-on:click='showModal("db")'>Joe S Gardner</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    import HttpService from '../services/HttpService'
    import router from '../router'
    export default {
        name: 'HeaderComponent',
        data: () => ({
            isShowDropdown: false,
            showModalDB : false,
            showModalS3 : false,
            uploadedFiles: [],
            dbData:{}
        }),
        methods: {
            showModal() {
                console.log(this.isShowDropdown);
                this.isShowDropdown = true
                console.log(this.isShowDropdown);
            },
            showModal(string){
                if ( string==='db' ){
                    this.showModalDB = this.showModalDB ? false : true;
                    document.querySelector('html').style.overflow = document.querySelector('html').style.overflow ? "hidden" : "initial";
                }
                if ( string==='s3' ){
                    return
                }
            },
            sendDbCredential(){
                let self = this;

                var obj = {
                    name: this.dbData.dbName,
                    type: this.dbData.dbType,
                    configuration: {
                        dsn: `${this.dbData.dbType}://${this.dbData.user}:${this.dbData.password}@${this.dbData.host}/${this.dbData.dbName}`
                    }
                }

                HttpService.methods.put('/sources', obj)
                    .then(function (response) {
                        alert('Data successfully added')
                        if(response.status===200){
                            router.push('/data-secrets')
                        }
                    })
                    .catch(function (error) {
                        console.log(error);
                    })
            }
        },
    }
</script>

<style scoped lang="less">
  .modal-db{
    position: absolute;
    width: 100%;
    height: 100%;
    top:0;
    left:0;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(247, 248, 252, 0.7);
    backdrop-filter: blur(6px);
    .modal-container{
      position: relative;
      padding: 40px;
      width: 490px;
      background-color: white;
      box-shadow: 0px 4px 15px rgba(189, 196, 224, 0.192);
      border-radius: 8px;
      .close{
        position: absolute;
        cursor: pointer;
        top: 20px;
        right: 20px;
        height: 20px;
        width: 20px;
        content: url(./../assets/img/icons/close.svg);
      }
      .modal-footer{
        button{
          width: 100%;
        }
      }
    }
  }
  .drag-drop,
  .sync{
    height: 306px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    cursor: pointer;
  }
  .sync-s-3{
    cursor: not-allowed;
  }
  .drag-drop{
    cursor: not-allowed;
    border: 2px dashed #9497A8;
    .description{
      margin-top: 30px;
      span{
        text-decoration: underline;
      }
      p{
        font-weight: 500;
        font-size: 16px;
        line-height: 24px;
      }
    }
    &:before{
      position: absolute;
      content: url(./../assets/img/images/drag-drop.svg);
      top: 70px;
      left: 50%;
      transform: translateX(-50%);
    }
  }
  .sync{
    background-color: white;
    box-shadow: 0px 4px 15px rgba(189, 196, 224, 0.192);
    .description{
      p{
        font-weight: 600;
        font-size: 16px;
        line-height: 25px;
        color: #9497A8;
      }
    }
  }
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

    .section {
      // width: 50%;
      // margin: 0 auto;
    }
  }
</style>
