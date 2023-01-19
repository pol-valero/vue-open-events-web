<script>

// We give to the singleton the data we want to share between components 
export default {
  name: "App",
  data() {
    return {
      user: {
        name: "User",
        image: "src/assets/default_img.png",
        id: 0,
      },
      show: {
        aside: true,
        header: true,
      },
      friendsRequests: [],
    };
  },



  methods: {
    // We log out the user and redirect him to the login page
    logout() {
      localStorage.removeItem("token");
      localStorage.removeItem("userInfo");
      this.$router.push("/login");
    },

    checkURL(url) {
    return(url.match(/\.(jpeg|jpg|gif|png)$/) != null);
    },

    getFriendsRequests(){
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/friends/requests'
      fetch(URL, {
        method: 'GET',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },     
      })
      .then(res => res.json())
      .then(res=> {
        let response = JSON.stringify(res);
        if(response.length > 0) {
          this.friendsRequests = res;
        }
      });
    },

    acceptFriendRequest(id){
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/friends/' + id;
      fetch(URL, {
        method: 'PUT',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },     
      })
      .then(this.getFriendsRequests()) // Update the friends requests
    },

    rejectFriendRequest(id){
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/friends/' + id;
      fetch(URL, {
        method: 'DELETE',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },     
      })
      .then(this.getFriendsRequests()) // Update the friends requests
    },

    showProfile() {
      this.$router.push(`/profile/${this.user.id}`);

      setTimeout(() => {
        window.location.reload();
      }, 50);

    }
  
  },

  //created lifecycle method
  mounted() {
    // If the user is logged in, we get the user info from local storage
    if (localStorage.getItem("userInfo")) {
      this.user.name = (JSON.parse(localStorage.getItem("userInfo"))[0].name).toUpperCase();
      this.user.id = JSON.parse(localStorage.getItem("userInfo"))[0].id;
      let img = JSON.parse(localStorage.getItem("userInfo"))[0].image;
      
      // We check if the image is a valid URL
      if(this.checkURL (img)){
        this.user.image = img;
      } else{
        this.user.image = "src/assets/default_img.png";
      }  
      this.getFriendsRequests();
      setInterval(this.getFriendsRequests, 5000); // We update the friends requests every 5 seconds

    } else {
      // If the user is not logged in, we redirect him to the login page
      this.$router.push("/login");
    }
  },

}
</script>
<script setup>
import { RouterLink, RouterView } from "vue-router";

</script>

<template>
  <!-- Make an v-if showing the content if showHeader is true -->
  <header v-if="show.header">
    <div id="top-header">
      <div id="title-logo">
        <img src="/src/assets/logo_image.png" alt="logo" class="header-img" />
        <h2 class="title">OPEN EVENTS</h2>
      </div>
      <!--<div id="user-photo" v-on:click="this.$router.push(`/profile/${user.id}`)">-->
      <button id="user-photo" v-on:click="showProfile()" >
        <h2 class="title">{{ user.name }}</h2>

        <!--
        <RouterLink id="profile-btn" to="/profile">
          <h2 class="title">{{ user.name }}</h2>
        </RouterLink>-->
        <img
          v-bind:src="user.image"
          onerror="this.src = 'src/assets/default_img.png'"
          alt="user photo"
          class="header-img"
        />
      </button>
    </div>

    <div id="bot-header">
      <input type="checkbox" id="check-box" />

      <nav id="barra-nav">
        <RouterLink id="barra-nav-home" class="std-padding" to="/"
          >HOME</RouterLink
        >
        <RouterLink id="barra-nav-discover" class="std-padding" to="/discover"
          >DISCOVER</RouterLink
        >
        <RouterLink id="barra-nav-friends" class="std-padding" to="/chat"
          >FRIENDS</RouterLink
        >

        <label for="check-box" id="hide-menu"></label>
      </nav>
      <label for="check-box" id="show-menu"></label>
    </div>
  </header>

  <div id="center-screen">
    <main>
      <!-- HERE ALL THE MAIN CODDE -->
      <RouterView />
    </main>

    <aside v-if="show.aside">
      <h3 class="title">REQUESTS</h3>

      <ul v-for="friend in friendsRequests" v-bind:key="friend.id">
        <li>
          <div class="request-container"> 
            <p id="name-request">{{ friend.name + " " + friend.last_name }}</p>
            <div id="answer-buttons">
              <button class="accept-button" v-on:click=acceptFriendRequest(friend.id)>Accept</button>
              <button class="reject-button" v-on:click=rejectFriendRequest(friend.id)>Reject</button>
            </div>
          </div>
        </li>
      </ul>
    </aside>
  </div>

  <footer>
    <h5 class="small-padding">Copyright <span> LaSalle 2022</span></h5>
  </footer>
</template>

<style scoped></style>
