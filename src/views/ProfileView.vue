<script>
export default {
  data(){
    return{
      text: "Sign In"
    }
  }, 

  methods: {},

  mounted(){
    const token = localStorage.getItem('token');
    fetch('http://puigmal.salle.url.edu/api/v2/users', {
      method: 'GET',
      headers:{
        'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
        'Content-Type': 'application/x-www-form-urlencoded'
      }
    })
    .then(res => res.json())
    .then(res=> {
          console.log(res);
    });

  }
  

}
</script>

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
      <table class="stats-table">
        <thead>
          <h1 id="statistics-title">Statistics</h1>
        </thead>
        <tbody>
          <tr>
            <td><h2>7.5</h2></td>
            <td><h2>201</h2></td>
            <td><h2>38%</h2></td>
          </tr>
          <tr>
            <td><h3>rating</h3></td>
            <td><h3>comments</h3></td>
            <td><h3>of users behind</h3></td>
          </tr>
        </tbody>
        <tfoot></tfoot>
      </table>
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
          <button class="logout-button primary-button">LOGOUT</button>
        </a>
        <button class="follow-button primary-button">FOLLOW</button>
        <a href="/editProfile">
          <button a class="edit-button secondary-button">EDIT</button>
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
  margin-top: 40px;
}

#profile-img {
  width: 120px;
  height: 120px;
  align-self: center;
}

.main-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: flex-start;
}

.profile-info {
  display: flex;
  justify-content: center;
  width: 100%;
}

.info-container {
  padding: 0px 20px;
}

.info-title {
  padding-bottom: 20px;
  padding-top: 20px;
}

.info-title ~ .info-title {
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
  flex-direction: column;
  align-items: center;
  padding: 40px 7px;
}

.edit-button {
  padding: 10px;
  width: 100px;
}

.logout-button {
  padding: 10px;
  width: 100px;
}

.follow-button {
  padding: 10px;
  width: 100px;
  margin: 15px 0px;
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

h2 {
  font-size: 20px;
}

h3 {
  font-weight: normal;
  font-size: 14px;
  padding-top: 5px;
}

td {
  padding-inline: 20px;
}

.stats-table {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
  text-align: center;
}

@media (min-width: 530px) {
  .main-container {
    justify-content: initial;
  }

  .profile-info {
    display: block;
    width: auto;
  }

  .info-container {
    padding: 0px 0px 0px 50px;
  }

  .info-title {
    padding-top: 0px;
  }

  .button-container {
    flex-direction: row;
    justify-content: space-evenly;
  }
  
  .follow-button {
    margin: 0px;
  }

  #profile-img {
    width: 200px;
    height: 200px;
  }

  h2 {
    font-size: revert;
  }

  td {
    padding-inline: 70px;
  }

  h3 {
    font-size: revert;
    padding-top: 0px;
  }
}
</style>
