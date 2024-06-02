<template>
	<div id="signin">
		<form class="row g-3" >
		  
		  
		 
		  <div class="col-md-6">
			<label for="email_input" class="form-label forms-text">Username</label>
			<input v-bind:value="email" v-on:change="email_input" type="text" class="form-control" id="email_input" required>
			<div class="valid-feedback">
			  Looks good!
			</div>
		  </div>
		  
		  <div class="col-md-3">
			<label for="password_input" class="form-label forms-text">Password</label>
			<input v-bind:value="password" v-on:change="password_input" type="password" class="form-control" id="password_input" required>
			<div class="invalid-feedback">
			  Please provide a password.
			</div>
		  </div>
		  
		  
		  <div class="col-12"></div>
					  
		  <div class="col-12">
			<div class="checkbox m-2 mb-3">
				<input v-bind:value="remember_me" v-model="remember_me" type="checkbox" value="remember-me" style="transform : scale(1.5);">
				<label class="text-center align-middle">
					 &nbsp; Remember me
				</label>
			</div>
			<button class="btn btn-primary" type="submit"  id="signin_button" @click="signin">Sign in</button>
		  </div>

		</form>
		  
	</div>
	
	
</template>
	


<script>
	import axios from "axios"
	export default {
		name: 'signin',
		//template: "<div>NAME {{ name }}</div>",
		// props: {
		// 	email: String,
		// 	password: String,
		// 	remember_me:Boolean,
		// },
		data() {
			return {
				email: "",
				password: "",
				remember_me: false,
			}
		},
		methods: {
			email_input(event) {
				this.email = event.target.value;
			},
			password_input(event) {
				this.password = event.target.value;
			},
			remember_me_input(event) {
				this.remember_me = event.target.value;
			},
			signin() {
				axios
				.get("http://localhost:3070/api/userdata", {
					params: {
						username: this.email,
						password: this.password,
					}
				}).then(response => {
					window.location.href = "/myaccount.html?username=" + this.email + "&" + "password=" + this.password;
				})
				.catch(err => {
					throw err;
				});
			},
			register() {

			},
		},
		mounted() {
			
		},
	}
</script>

<style>
	
</style>
