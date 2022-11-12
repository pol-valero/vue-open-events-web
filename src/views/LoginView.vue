<template>
  <div id="image-box">
    <img id="logo-image" src="src/assets/logo_image.png" />
  </div>

  <div id="main-login-box">
    <div class="login-box">
      <form action="">
        <h1>Login</h1>
        <input
          class="icon_message"
          type="text"
          name="email"
          id="email"
          required
          placeholder="abc@email.com"
        />
        <input
          class="icon_lock"
          type="password"
          name="password"
          id="password"
          required
          placeholder="Your password"
        />
        <div>
          <input id="button-sign-in" type="submit" value="Sign In" />
        </div>
        <div>
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
}
.login-box {
  padding: 30px;
  width: 250px;
  margin-top: 50px;
  text-align: center;
  background-color: rgb(203, 208, 206);
  border-radius: 10px;
  margin: 50px;
}

#main-login-box {
  display: flex;
  justify-content: center;
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
  padding-top: 80px;
  padding-bottom: 20px;
}

#logo-image {
  width: 100px;
  height: 100px;
  scale: 2;
}

#button-sign-in {
  background-color: black;
  color: white;
  border-radius: 10px;
  height: 30px;
  width: 170px;
  margin: 10px;
}

#button-sign-in:hover {
  background-color: #5a5a5a;
  transition: 0.4s;
}

#nav-login {
  border: none;
  background: none;
  text-decoration: none;
  color: #25d366;
}

#nav-login:hover {
  color: black;
  transition: 0.4s;
  cursor: pointer;
}

@media (max-width: 530px) {
  .login-box {
    padding: 15px;
  }
  #logo-image {
    scale: 1.2;
  }
  #image-box {
    padding-top: 40px;
    padding-bottom: 0px;
  }
}
</style>
