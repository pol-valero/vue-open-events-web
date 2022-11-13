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
            <input id="input-user-name" type="text" name="name" required placeholder="Name">            
            <input id="input-user-lastname" type="text" name="last-name" required placeholder="Last Name">            
          </div>
          
          <input id="input-user-email" type="text" name="email" required placeholder="abc@email.com">            
          <input id="input-password" type="password" name="password" required placeholder="Password">            
          <input id="input-confirm-password" type="password" name="confirm-password" required placeholder="Confirm Password">            
          <input id="input-birth-date" type="text" name="birth-date" required placeholder="Birth date">            
          <input id="input-profile-picture" type="text" name="profile-picture" required placeholder="Profile picture">            
        </div>
              
        <div>
          <input id="button-sign-up" type="submit" value="Register">        
        </div>
        
        <div id="login-link-box">
          <label>Already registered? </label>
          <RouterLink id="nav-signup" to="/login">Login</RouterLink>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.input-margin {
  margin: 10px;
}

.register-box {
  display: flex;
  flex-direction: column;
  padding: 30px 15px;    
  width: 60%;
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
  width: 60%;
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
  width: 33%;
}

#input-user-lastname {
  background: url(src/assets/icon_user.svg) no-repeat scroll;
  width: 33%;
}

#input-user-email {
  background: url(src/assets/icon_message.svg) no-repeat scroll;
  width: 89%;
}

#input-password {
  background: url(src/assets/icon_lock.svg) no-repeat scroll;
  width: 89%;
}

#input-confirm-password {
  background: url(src/assets/icon_lock.svg) no-repeat scroll;
  width: 89%;
}

#input-birth-date {
  background: url(src/assets/icon_calendar.svg) no-repeat scroll;
  width: 89%;
}

#input-profile-picture {
  background: url(src/assets/icon_image.svg) no-repeat scroll;
  width: 89%;
}

#image-box {
  display: flex;
  justify-content:center;
  padding-top: 40px;
  padding-bottom: 0px;
}

#logo-image {
  width: 100px;
  height: 100px;
}

#button-sign-up {
  background-color: black;
  color: white;
  border-radius: 10px;
  border: none;
  height: 30px;
  width: 170px;
  margin: 10px;
  cursor: pointer;
  transition: 0.1s;
}

#button-sign-up:hover {
  background-color: #7722ff;
  opacity: 1;
  box-shadow: 4px 5px 5px rgba(0, 0, 0, 0.5);
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
    width: 70%;
    padding: 30px;
  }

  #signup-heading {
    font-size: default;
  }

  #input-user-fullname {
    justify-content: space-between;
    flex-wrap: wrap;
  }
}
</style>