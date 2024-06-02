<template>
	
 <div>
   <form class="row g-3 needs-validation" >
      <div v-bind:value="username" v-on:change="username_input" class="col-md-4">
        <label for="user_name_input" class="form-label forms-text">First name</label>
        <input type="text" class="form-control" id="user_name_input" required>
        <div class="valid-feedback">
          Looks good!
        </div>
      </div>
      <div v-bind:value="birthdate" v-on:change="birthdate_input" class="col-md-4">
        <label for="birthdate_input" class="form-label forms-text">Birth date</label>
        <input type="date" class="form-control" id="birthdate_input" required>
        <div class="valid-feedback">
          Looks good!
        </div>
      </div>
      <div class="col-md-4">
        <label for="sex_input" class="form-label forms-text">Sex</label>
        <select v-bind:value="sex" v-model="sex" class="form-select" id="sex_input" required>
          <option selected disabled value="">Choose...</option>
              <option>Unknown</option>
							<option>Male</option>
							<option>Female</option>
        </select>

        <div class="invalid-feedback">
          Please select a valid state.
        </div>
      </div>
      <div v-bind:value="email" v-on:change="email_input" class="col-md-6">
        <label for="email_input" class="form-label forms-text">Email adress</label>
        <input type="email" class="form-control" id="email_input" required>
        <div class="valid-feedback">
          Looks good!
        </div>
      </div>
      
      <div class="col-md-3">
        <label for="password_input" class="form-label forms-text">Password</label>
        <input v-bind:value="password" v-on:change="password_input" type="password" class="form-control" id="password_input" required>
        <div class="invalid-feedback">
          Please provide a valid password.
        </div>
      </div>
      
      <div class="col-md-3">
        <label for="repeat_password" class="form-label forms-text">Repeat Password</label>
        <input v-bind:value="repeat_password" v-on:change="repeat_password_input" type="password" class="form-control" id="repeat_password" required>
        <div class="invalid-feedback">
          Please provide a valid password.
        </div>
      </div>
      <div class="col-12"></div>
        
      
      <div class="col-12">
        <button  @click="register" type="button" id="register_button" class="btn btn-primary" >Register</button>
      </div>
    </form>

  </div>

		
	
</template>

<script>
	import axios from "axios"
	export default {
		name: 'register',
		//template: "<div>NAME {{ name }}</div>",
		// props: {
		// 	email: String,
		// 	password: String,
		// 	remember_me:Boolean,
		// },
		data() {
			return {
				username: "",
				birthdate: "",
				sex: "",
				email: "",
				password: "",
				repeat_password: "",
			}
		},
		methods: {
			username_input(event) {
				this.username = event.target.value;
			},
			birthdate_input(event) {
				this.birthdate = event.target.value;
			},
			sex_input(event) {
				this.birthdate = event.target.value;
			},
			email_input(event) {
				this.email = event.target.value;
			},
			password_input(event) {
				this.password = event.target.value;
			},
			repeat_password_input(event) {
				this.repeat_password = event.target.value;
			},
			signin() {
				
			},
			register() {
				axios
				.post("http://localhost:3070/api/register", {
					data: JSON.parse(JSON.stringify(this))
				}).then(response => {
					console.log(response.data)
					//this.results = response.data[1];
					//console.log(this.results);
					window.location.href = "/myaccount.html?username=" + this.username + "&" + "password=" + this.password;
				}).catch(err => {
					throw err;
				});
				/*fetch("http://localhost:3070/api/register", {
						method: "POST",
						body: JSON.stringify(this),
						headers: {
						"Content-Type": "application/json",
					},
				}).then().catch();*/
				
			},
		},
		mounted() {
			
		},
	}
</script>

<style>
	
</style>
