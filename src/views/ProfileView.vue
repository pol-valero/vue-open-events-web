<script>
export default {
    data() {
        return {
            userID: this.$route.params.userID,
            //userID: -1,
            userName: "",
            userLastName: "",
            userEmail: "",
            userImage: "",
            rating: 0,
            comments: 0,
            usersBehind: 0,
            show: false,
        };
    },
    methods: {
        checkURL(url) {
            return (url.match(/\.(jpeg|jpg|gif|png)$/) != null);
        },
        logout() {
            localStorage.removeItem("token");
            localStorage.removeItem("userInfo");
            this.$router.push("/login");
        },
        followUser() {
            const token = localStorage.getItem("token");
            fetch("http://puigmal.salle.url.edu/api/v2/friends/" + this.userID, {
                method: "POST",
                headers: {
                    "Authorization": "Bearer " + JSON.parse(token).accessToken,
                    "Content-Type": "application/json",
                },
            })
                .then(alert("Friend request sended!"));
        }
    },
    // TODO: In case you are already in /profile:id and you want to go to /profile
    mounted() {
        //Getting the user's token
        const token = localStorage.getItem("token");
        var localUserID = JSON.parse(localStorage.getItem("userInfo"))[0].id;
        //console.log("localUserID: " + localUserID);
        //console.log("this.userID: " + this.userID);
        // Case when profile is the user's own profile
        if (this.userID == localUserID) {
            this.show = true;
            //Getting the user's info
            this.userID = JSON.parse(localStorage.getItem("userInfo"))[0].id;
            this.userName = JSON.parse(localStorage.getItem("userInfo"))[0].name;
            this.userLastName = JSON.parse(localStorage.getItem("userInfo"))[0].last_name;
            this.userEmail = JSON.parse(localStorage.getItem("userInfo"))[0].email;
            this.userImage = JSON.parse(localStorage.getItem("userInfo"))[0].image;
        }
        else {
            this.show = false;
            // Case when profile is another user's profile
            fetch("http://puigmal.salle.url.edu/api/v2/users/" + this.userID, {
                method: "GET",
                headers: {
                    "Authorization": "Bearer " + JSON.parse(token).accessToken,
                    "Content-Type": "application/json",
                },
            })
                .then(res => res.json())
                .then(res => {
                if (res) { // check if the response is not empty
                    this.userID = res[0].id;
                    this.userName = res[0].name;
                    this.userLastName = res[0].last_name;
                    this.userEmail = res[0].email;
                    this.userImage = res[0].image;
                }
            });
        }
        fetch("http://puigmal.salle.url.edu/api/v2/users/" + this.userID + "/statistics", {
            method: "GET",
            headers: {
                "Authorization": "Bearer " + JSON.parse(token).accessToken,
                "Content-Type": "application/json",
            },
        })
            .then(res => res.json())
            .then(res => {
            if (res) {
                // check if the response is not null
                res[0].avg_score == null ? res[0].avg_score = 0 : this.rating = res[0].avg_score;
                res[0].num_comments == null ? res[0].num_comments = 0 : this.comments = res[0].num_comments;
                res[0].percentage_commenters_below == null ? res[0].percentage_commenters_below = 0
                    : this.usersBehind = res[0].percentage_commenters_below;
            }
        });
    },
}
</script>

<template>
  <div id="profile-main">
    <section id="container-full-profile">
      <h1 id="profile-title">Profile</h1>

      <div class="main-container">
        <div class="profile-info">
          <img 
          onerror="this.src = 'src/assets/default_img.png'"
          v-bind:src="userImage" 
          alt="logo" 
          id="profile-img"/>
        </div>

        <div class="info-container">
          <h2 class="info-title">Name</h2>
          <p class="user-name">{{userName + " " + userLastName}}</p>
          <h2 class="info-title">Email</h2>
          <p class="user-name">{{userEmail}}</p>
        </div>
      </div>
    </section>

    <section id="container-full-profile">
      <h1 id="statistics-title">Statistics</h1>
      <table class="stats-table">
        <tbody>
          <tr>
            <td><h2>{{ rating }}</h2></td>
            <td><h2>{{ comments }}</h2></td>
            <td><h2>{{ usersBehind + "%" }}</h2></td>
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
        <a href="/login"  v-if="show">
          <button v-on:click="logout()" class="logout-button primary-button">LOGOUT</button>
        </a>
        <button v-on:click="followUser()" class="follow-button primary-button" v-if="!show">FOLLOW</button>
        <a href="/editProfile">
          <button a class="edit-button secondary-button" v-if="show">EDIT</button>
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
