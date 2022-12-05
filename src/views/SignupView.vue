<script>
export default {

  methods: {
    signup(){
      fetch('http://puigmal.salle.url.edu/api/v2/users', {
        method: 'POST',
        headers:{
          'Content-Type': 'application/x-www-form-urlencoded'
        },    
        body: new URLSearchParams(
          { 
            name: document.getElementById('input-user-name').value,
            last_name: document.getElementById('input-user-lastname').value,
            email: document.getElementById('input-user-email').value, 
            password: document.getElementById('input-password').value,
            image: document.getElementById('input-profile-picture').value
          })
      })
      .then(res => res.json())
      .then(res=> {
            console.log(res);
      });

    }
  }

}
</script>

<template>
  <div id="image-box">
    <img id="logo-image" src="src/assets/logo_image.png" />
  </div>

  <div id="main-register-box">
    <div class="register-box">
      <form action="">
        <h1 id="signup-heading">Signup</h1>
        <div id="signup-fields-box">
          <div id="input-user-fullname">
            <input
              id="input-user-name"
              type="text"
              name="name"
              required
              placeholder="Name"
            />
            <input
              id="input-user-lastname"
              type="text"
              name="last-name"
              required
              placeholder="Last Name"
            />
          </div>
          <div id="remaining-fields">
            <input
              id="input-user-email"
              type="text"
              name="email"
              required
              placeholder="abc@email.com"
            />
            <input
              id="input-password"
              type="password"
              name="password"
              required
              placeholder="Password"
            />
            <input
              id="input-profile-picture"
              type="text"
              name="profile-picture"
              required
              placeholder="Profile picture"
            />
          </div>
        </div>
        <!--<div>
          <input id="button-sign-up" class="primary-button" type="submit" value="Register"/>
        </div>-->
        <div id="login-link-box">
          <label>Already registered? </label>
          <RouterLink id="nav-signup" to="/login">Login</RouterLink>
        </div>
      </form>
      <button v-on:click="signup()" class="primary-button" type="submit" value="Register" id="signup-button">Signup</button>
    </div>
  </div>
</template>

<style scoped>
.register-box {
  display: flex;
  flex-direction: column;
  padding: 30px 15px;
  width: 70%;
  justify-content: center;
  text-align: center;
  background-color: #eeeeff;
  border-radius: 10px;
  margin: 50px 0px 80px 0px;
}

#main-register-box {
  display: flex;
  justify-content: center;
}

#signup-fields-box {
  padding: 30px 10px 10px 10px;
}

#signup-fields-box input {
  background-color: white;
  border: #ccc solid 2px;
  border-radius: 10px;
  background-size: 20px;
  background-position: 8px;
  padding: 7px 15px 7px 40px;
  margin-bottom: 15px;
}

#signup-fields-box input:focus {
  border-color: #7722ff;
  outline: none;
}

#input-user-fullname {
  display: flex;
  flex-direction: column;
  align-content: center;
}

#input-user-name {
  background: url(src/assets/icon_user.svg) no-repeat scroll left;
}

#input-user-lastname {
  background: url(src/assets/icon_user.svg) no-repeat scroll;
}

#remaining-fields {
  display: flex;
  flex-direction: column;
}

#input-user-email {
  background: url(src/assets/icon_message.svg) no-repeat scroll;
}

#input-password {
  background: url(src/assets/icon_lock.svg) no-repeat scroll;
}

#input-confirm-password {
  background: url(src/assets/icon_lock.svg) no-repeat scroll;
}

#input-birth-date {
  background: url(src/assets/icon_calendar.svg) no-repeat scroll;
}

#input-profile-picture {
  background: url(src/assets/icon_image.svg) no-repeat scroll;
}

#image-box {
  display: flex;
  justify-content: center;
  padding-top: 40px;
  padding-bottom: 0px;
}

#logo-image {
  width: 100px;
  height: 100px;
}

#button-sign-up {
  height: 30px;
  width: 170px;
  margin: 10px;
}

#login-link-box {
  padding-top: 10px;
}

#nav-signup {
  border: none;
  background: none;
  text-decoration: underline;
  color: #7722ff;
  cursor: pointer;
}

#nav-signup:hover {
  color: black;
  transition: 0.2s;
}

#signup-heading {
  font-size: 26px;
}

@media (min-width: 530px) {
  #image-box {
    padding-top: 80px;
    padding-bottom: 20px;
  }

  #logo-image {
    width: 150px;
    height: 150px;
  }

  .register-box {
    width: 50%;
    padding: 30px;
  }

  #signup-heading {
    font-size: default;
  }

  #remaining-fields input {
    width: auto;
  }

  #input-user-fullname {
    flex-direction: row;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  #input-user-fullname input {
    width: 33%;
  }
}
</style>
