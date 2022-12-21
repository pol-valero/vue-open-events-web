<script>
export default {
  data(){
    return{
      userName: "",
      userLastName: "",
      userEmail: "",
      //userPassword: "",
      //userConfirmedPassword: "",
      userImage: "",
    }
  }, 

  methods: {
    editProfile(){

      // Checking if the name and last name are alphanumeric
      if (!(document.getElementById('name-input').value).match(/^[0-9a-z]+$/)){
        alert("Name must be alphanumeric");
        return;
      }

      // Checking if the fields are empty
      if(document.getElementById('name-input').value == "" 
      || document.getElementById('lastname-input').value == "" 
      || document.getElementById('email-input').value == "" 
      || document.getElementById('password-input').value == "" 
      || document.getElementById('confirmed-password-input').value == ""
      || document.getElementById('image-input').value == ""){
        alert("All fields must be filled");
        return;
      }

      // Checking if the password is at least 8 characters long
      if(document.getElementById('password-input').value.length < 8){
        alert("Password must be at least 8 characters long");
        return;
      }

      // Checking if the password and confirmed password match
      if((document.getElementById('password-input').value).
      localeCompare(document.getElementById('confirmed-password-input').value) != 0){
        alert("Passwords don't match");
        return;
      }

      //Getting the user's token
      const token = localStorage.getItem('token');

      fetch('http://puigmal.salle.url.edu/api/v2/users/', {
        method: 'PUT',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json'
        },    
        body: JSON.stringify(
          { 
            name: document.getElementById('name-input').value, 
            last_name: document.getElementById('lastname-input').value,
            email: document.getElementById('email-input').value,
            password: document.getElementById('password-input').value,
            image: document.getElementById('image-input').value
          })
      })

      let user = JSON.parse(localStorage.getItem("userInfo"));
      user[0].name = document.getElementById('name-input').value;
      user[0].last_name = document.getElementById('lastname-input').value;
      user[0].email = document.getElementById('email-input').value;
      user[0].image = document.getElementById('image-input').value;
      localStorage.removeItem('userInfo');
      localStorage.setItem('userInfo', JSON.stringify(user));

      // Updating the user's info from App.vue
      this.$root.$data.user.name = (JSON.parse(localStorage.getItem("userInfo"))[0].name).toUpperCase();
      this.$root.$data.user.image = JSON.parse(localStorage.getItem("userInfo"))[0].image;
      this.$router.push('/profile');      
    },
    deleteProfile(){
      //Getting the user's token
      const token = localStorage.getItem('token');

      fetch('http://puigmal.salle.url.edu/api/v2/users/', {
        method: 'DELETE',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json'
        },
      })

      // We remove the token and the user's info from localStorage
      .then(
        localStorage.removeItem("token"),
        localStorage.removeItem("userInfo"),
        this.$router.push("/login"),
        alert("Account successfully deleted")
      )
    }
  },

  mounted(){
    // Getting the user's info
    this.userName = JSON.parse(localStorage.getItem("userInfo"))[0].name;
    this.userLastName = JSON.parse(localStorage.getItem("userInfo"))[0].last_name;
    this.userEmail = JSON.parse(localStorage.getItem("userInfo"))[0].email;
    this.userImage = JSON.parse(localStorage.getItem("userInfo"))[0].image;
    
    // Set placeholders from user's info
    document.getElementById('name-input').value = this.userName;
    document.getElementById('lastname-input').value = this.userLastName;
    document.getElementById('email-input').value = this.userEmail;
    document.getElementById('image-input').value = this.userImage;
  
    // We hide the aside
    this.$root.$data.show.aside = false;
  }
  

}
</script>

<template>
  <div id="edit-profile-main">
    <section id="title-container">
      <h2>Edit profile</h2>
    </section>

    <section id="forms-container">
      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Name</h4>
          <input id="name-input" class="field" type="text" placeholder="Name" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Lastname</h4>
          <input id="lastname-input" class="field" type="text" placeholder="Lastname" />
        </div>
      </div>

      <div class="single-form">
        <h4 class="form-title">Email</h4>
        <input id="email-input" class="field" type="text" placeholder="Ex.- email@gmail.com" />
      </div>

      <div class="single-form">
        <h4 class="form-title">Password</h4>
        <input
          id="password-input"
          class="field"
          type="password"
          placeholder="&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;"
        />
      </div>

      <div class="single-form">
        <h4 class="form-title">Confirm password</h4>
        <input
          id="confirmed-password-input"
          class="field"
          type="password"
          placeholder="&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;"
        />
      </div>

      <!--
      <div class="single-form">
        <h4 class="form-title">Birth date</h4>
        <input class="field" type="date" />
      </div>-->

      <div class="single-form">
        <h4 class="form-title">Image</h4>
        <input id="image-input" class="field" type="text" placeholder="www.salleurl.edu/salle_en.png" />
      </div>
      <!--
      <nav id="delete-account-link">
        <RouterLink id="nav-delete-account" to="/">Delete account</RouterLink>
      </nav>--> 
      
      <nav id="nav-delete-account" v-on:click="deleteProfile()">Delete account</nav>

      <div class="button-container">
        <!--
        <button
          onclick="location.href='/profile';"
          class="save-button primary-button"
        >
          SAVE CHANGES
        </button>
        -->
        <button v-on:click="editProfile()" class="save-button primary-button">SAVE CHANGES</button>


        <button
          onclick="location.href='/profile';"
          class="cancel-button secondary-button"
        >
          CANCEL
        </button>
      </div>
    </section>
  </div>
</template>

<style scoped>
#edit-profile-main {
  width: 100%;
  height: 100%;
  flex-direction: column;
  display: flex;
}

#title-container {
  margin-top: 30px;
  margin-bottom: 20px;
  text-align: center;
  font-size: 15px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

#forms-container {
  display: flex;
  flex-direction: column;
  width: 180px;
  align-self: center;
  padding: 30px;
  background-color: #eeeeff;
  border-radius: 10px;
  margin-bottom: 50px;
}

.single-form {
  display: flex;
  flex-direction: column;
  margin: 5px;
}

.dual-form {
  display: flex;
  flex-flow: row wrap;
}

.dual-form div {
  flex-grow: 1;
}

.button-container {
  margin: 30px;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-evenly;
}

.save-button {
  height: 50px;
  width: 170px;
  margin: 10px;
}

.cancel-button {
  height: 50px;
  width: 170px;
  margin: 10px;
}

#delete-account-link {
  margin-top: 20px;
}

#nav-delete-account {
  border: none;
  background: none;
  text-decoration: underline;
  color: black;
  cursor: pointer;
}

#nav-delete-account:hover {
  color: #d40303;
  transition: 0.1s;
}

@media (min-width: 650px) {
  #forms-container {
    width: 40%;
  }
}
</style>
