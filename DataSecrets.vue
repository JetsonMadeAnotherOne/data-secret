<template>
	<div>
		<HeaderComponent/>
		<div class="headers">
			<h1>Data Secrets</h1>
			<button
				class='button-main'
				@click="goTo(`/data-secrets/add`,false)"
			>
				Add a data source
			</button>
		</div>
		<div class="table">
			<v-data-table
				:headers="dataSecretsTableHeaders"
				:items="dataSecrets"
				:items-per-page="7"
				class="table"
			>
				<template v-slot:item.action="{ item }">
					<v-icon
						small
						class="mr-2"
						@click="editItem(item)"
					>
						edit
					</v-icon>
					<v-icon
						small
            class="dl"
						@click="deleteItem(item)"
					>
						delete
					</v-icon>
				</template>
				<template v-slot:item.button="{ item }">
					<button
						class='button-secondary'
						@click="goTo(`/data-secrets/analytics/${item.id}`,item)"
					>
						View Analytics
					</button>
				</template>
			</v-data-table>
		</div>
	</div>
</template>

<script>
	import HeaderComponent from '@/components/header.vue'
	import HttpService from '../services/HttpService'
	import router from '@/router'

console.log(HttpService);

	export default {
		name: 'DataSecrets',
		data: () => ({
			dataSecretsTableHeaders: [
		        { text: 'DATA SOURCE', value: 'name' },
		        { text: 'UPDATED', value: 'created' },
		        { text: 'TYPE OF DATA', value: 'type' },
		        { text: 'STATUS', value: 'status' },
		        { text: 'ACTION', value: 'action', sortable: false },
		        { text: '', value: 'button', sortable: false  },
		    ],
			dataSecrets: []
		}),
		components: {
			HeaderComponent
		},
		methods: {
			getDataSecrets () {
				let self = this;
				HttpService.methods.post('/sources')
					.then(function (response) {
						self.dataSecrets = response['data']['data'];
					})
					.catch(function (error) {
						console.log(error);
					})

			},
			editItem(item){
				console.log(item);
				// this.dataSecrets.indexOf(item)
			},
			deleteItem(item){
				var self = this
				console.log(item.id);
				// HttpService.methods.delete('/sources/' + item.id)
				// 	.then(function (response) {
				// 		console.log(response);
				// 		self.getDataSecrets()
				// 	})
				// 	.catch(function (error) {
				// 		console.log(error);
				// 	})
			},
			goTo(route, item){
				console.log(route,item);
				if(item){
					router.push({
						path: route,
						params: { dataSecret: `${item.id}`}
					})
				} else {
					router.push({
						path: route
					})
				}
			},
		},
		created: function(){
			if(!this.$store.state.basicUrl, !this.$store.state.guardKey, !this.$store.state.headers){
				this.goTo('/login')
			} else {
				this.getDataSecrets()
			}
		}
	}
</script>

<style lang="less">

	.headers{
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 80px;
	}
	.table{
    .mr-2{
      content: url(./../assets/img/icons/edit_no_active.png);
      cursor: pointer;
      margin-right: 15.71px;
      &:hover{
        content: url(./../assets/img/icons/edit_active.png);
        cursor: pointer;
      }
    }
    .dl{
      content: url(./../assets/img/icons/delete_no_active.png);
      cursor: pointer;
      &:hover{
        content: url(./../assets/img/icons/delete_active.png);
        cursor: pointer;
      }
    }
		.v-data-table {
			.v-data-table__wrapper{
				table{
					border-collapse:separate;
					border-spacing: 0 1em;
          //background: red;
				}
			}
			.v-data-footer__select{
				display: none !important;
			}
			tr{
        background: #F0F1F7;
        border-radius: 7px;
			}
      td{
        font-family: Poppins;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        color: #4D526E;
      }
      th{
        span{
          font-family: Poppins;
          font-style: normal;
          font-weight: bold;
          font-size: 12px;
          text-transform: uppercase;
          color: #878AA0;
        }
      }

		}
	}
</style>
