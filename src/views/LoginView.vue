<template>
  <div id="image-box">
    <img id="logo-image" src="src/assets/logo_image.png" />
  </div>

  <div id="main-login-box">
    <div class="login-box">
      <form action="">
        <h1 id="login-heading">Login</h1>
        <div id="signup-fields">
          <input
            class="icon_message"
            type="text"
            name="email"
            id="login-email"
            required
            placeholder="abc@email.com"
          />
          <input
            class="icon_lock"
            type="password"
            name="password"
            id="login-password"
            required
            placeholder="Your password"
          />
          <input
            id="button-sign-in"
            class="primary-button"
            type="submit"
            value="Sign In"
          />
        </div>
        <div id="signup-link-box">
          <label>Not registered? </label>
          <RouterLink id="nav-login" to="/signup">Signup</RouterLink>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
input {
  margin: 10px;
  border: #ccc solid 2px;
}

input:focus {
  border-color: #7722ff;
  outline: none;
}

#signup-link-box {
  padding: 10px;
}

#signup-fields {
  margin-top: 20px;
}

.login-box {
  padding: 30px 15px;    
  width: 250px;
  text-align: center;
  background-color: #eeeeff;
  border-radius: 10px;
  margin: 50px 50px 80px 50px;
}

#main-login-box {
  display: flex;
  justify-content:center;
}

.icon_message {
  background: url(src/assets/icon_lock.svg) no-repeat scroll left;
  background-size: 20px;
  background-position: 8px;
  padding-left: 30px;
  background-color: white;
  border-radius: 10px;
  margin-bottom: 7px;
  margin-top: 15px;
  padding-block: 7px;
  padding-inline: 40px;
}

.icon_lock {
  background: url(src/assets/icon_message.svg) no-repeat scroll;
  background-size: 20px;
  background-position: 8px;
  padding-left: 30px;
  background-color: white;
  border-radius: 10px;
  margin-bottom: 5px;
  padding-block: 7px;
  padding-inline: 40px;
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

#button-sign-in {
  height: 30px;
  width: 170px;
  margin: 30px 10px 10px 10px;
  border: none;
}

#nav-login {
  border: none;
  background: none;
  text-decoration: underline;
  color: #7722ff;
  cursor: pointer;
}

#nav-login:hover {
  color: black;
  transition: 0.2s;
}

@media (min-width: 530px) {
  .login-box {
    padding: 30px;
  }

  #logo-image {
    width: 150px;
    height: 150px;
  }

  #image-box {
    padding-top: 80px;
    padding-bottom: 20px;
  }

  #login-heading {
    font-size: default;
  }
}
</style>
