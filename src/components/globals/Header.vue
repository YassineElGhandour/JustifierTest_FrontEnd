<template>
	<v-toolbar fixed class="blue-grey lighten-2
		" dark>

		<v-toolbar-title class="mr-4">
			<span class="home"
				@click="navigateTo({name : 'root'})">	
					Justify
			</span>
		</v-toolbar-title>

		<v-toolbar-items>
			<v-btn
				v-if="$store.state.isUserLoggedIn"
				flat dark
				@click="navigateTo({name: 'songs'})"
				>
				Browse
			</v-btn>
		</v-toolbar-items>

		<v-spacer></v-spacer>

		<v-toolbar-items>
			<v-btn 
				v-if="!$store.state.isUserLoggedIn"
				flat dark
				@click="navigateTo({name: 'login'})">
					Login
			</v-btn>
		</v-toolbar-items>

		<v-toolbar-items>
			<v-btn 
				v-if="!$store.state.isUserLoggedIn"
				flat dark
				@click="navigateTo({name: 'register'})">
					Sign Up
			</v-btn>
		</v-toolbar-items>
		
		<v-toolbar-items>
			<v-btn 
				v-if="$store.state.isUserLoggedIn"
				flat dark
				@click="navigateTo({name: 'logout'})">
					Log out
			</v-btn>
		</v-toolbar-items>

	</v-toolbar>
</template>

<script>
	export default {
		methods: {
			navigateTo (route) {
				this.$router.push(route)
			},
			logout () {
				this.$store.dispatch('setToken', null)
				this.$store.dispatch('setUser', null)
				this.$router.push({
					name: 'root'
				})
			}
		}
	}
</script>

<style scoped>
	.home{
		cursor : pointer;
	}
	.home:hover {
		color: #E9E;
	}
</style>