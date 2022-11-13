<template>
  <div id="profile-main">
    <section id="container-full-profile">
      <h1 id="profile-title">Profile</h1>

      <div class="main-container">
        <div class="profile-info">
          <img id="profile-img" src="../assets/default_img.png" alt="logo" />
        </div>

        <div class="info-container">
          <h2 class="info-title">Name</h2>
          <p class="user-name">Firstname Lastname</p>
          <h2 class="info-title">Email</h2>
          <p class="user-name">email@email.com</p>
        </div>
      </div>
    </section>

    <section id="container-full-profile">
      <h1 id="statistics-title">Statistics</h1>

      <div class="statistics-container">
        <div class="info-component">
          <h2>7.5</h2>
          <h3>rating</h3>
        </div>
        <div class="info-component">
          <h2>201</h2>
          <h3>comments</h3>
        </div>
        <div class="info-component">
          <h2>38%</h2>
          <h3>of users behind you</h3>
        </div>
      </div>
    </section>

    <section id="container-full-profile">
      <nav>
        <RouterLink id="nav-timeline" to="/timeline">View timeline</RouterLink>
      </nav>
    </section>

    <section id="container-full-profile">
      <div class="button-container">
        <!--TEMPORAL PER HTML I CSS-->
        <a href="/login">
          <button class="logout-button">LOGOUT</button>
        </a>
        <a href="/editProfile">
          <button a class="edit-button">EDIT</button>
        </a>
      </div>
    </section>
  </div>
</template>

<style scoped>
#profile-main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  display: block;
}

#profile-title {
  margin-bottom: 20px;
}

#statistics-title {
  margin-bottom: 20px;
  margin-top: 20px;
}

#profile-img {
  width: 250px;
  height: 250px;
}

.main-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.info-container {
  padding-left: 50px;
}

.info-title {
  padding-bottom: 20px;
  padding-top: 20px;
}

.statistics-container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  padding: 20px;
}

.button-container {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  padding: 7px;
}

.edit-button {
  background-color: #fefefe;
  border-radius: 10px;
  border: #7722ff solid 2px;
  color: #7722ff;
  padding: 10px;
  width: 100px;
  transition: 0.1s;
}

.edit-button:hover {
  box-shadow: inset 0px 0px 5px 2px rgba(0, 0, 0, 0.3);
}

.logout-button {
  padding: 10px;
  background-color: black;
  color: #fff;
  border-radius: 10px;
  border: none;
  width: 100px;
  transition: 0.1s;
}

.logout-button:hover {
  background-color: #7722ff;
  opacity: 1;
  box-shadow: 4px 5px 5px rgba(0, 0, 0, 0.5);
}

.info-component {
  text-align: center;
}

.info-component h3 {
  font-size: 15px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

#container-full-profile {
  margin: 20px;
}

#nav-timeline {
  border: none;
  background: none;
  text-decoration: underline;
  color: black;
}

#nav-timeline:hover {
  color: #7722ff;
  transition: 0.2s;
  cursor: pointer;
}
</style>
