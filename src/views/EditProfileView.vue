<template>
  <div id="edit-profile-main">
    <section id="title-container">
      <h2>Edit profile</h2>
    </section>

    <section id="forms-container">
      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Name</h4>
          <input class="field" type="text" placeholder="Firstname" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Lastname</h4>
          <input class="field" type="text" placeholder="Lastname" />
        </div>
      </div>

      <div class="single-form">
        <h4 class="form-title">Email</h4>
        <input class="field" type="text" placeholder="Ex.- email@gmail.com" />
      </div>

      <div class="single-form">
        <h4 class="form-title">Password</h4>
        <input
          class="field"
          type="password"
          placeholder="&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;"
        />
      </div>

      <div class="single-form">
        <h4 class="form-title">Confirm password</h4>
        <input
          class="field"
          type="password"
          placeholder="&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;"
        />
      </div>

      <div class="single-form">
        <h4 class="form-title">Birth date</h4>
        <input class="field" type="date" />
      </div>

      <nav id="delete-account-link">
        <RouterLink id="nav-delete-account" to="/">Delete account</RouterLink>
      </nav>

      <div class="button-container">
        <button onclick="location.href='/profile';" class="save-button primary-button">
          SAVE CHANGES
        </button>
        <button onclick="location.href='/profile';" class="cancel-button secondary-button">
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
  width: 30%;
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

@media (max-width: 650px) {
  #forms-container {
    width: 180px;
  }
}
</style>
