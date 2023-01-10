<script>

// We give to the singleton the data we want to share between components 
export default {
  name: "App",
  data() {
    return {
      user: {
        name: "User",
        image: "src/assets/default_img.png",
      },
      show: {
        aside: true,
        header: true,
      },
      eventToDisplay: {
        title: 'Title',
        description: 'Description',
        startDate: '2023-06-22T08:22:00.000Z',
        endDate: '2023-06-23T10:45:00.000Z',
        location: 'Location name',
        image:'src/assets/event-details-background.png',
        type:'Type',
        capacity: 0,
        organizer:'Firstname Lastname'
      }
    };
  },

  //created lifecycle method
  mounted() {
    // If the user is logged in, we get the user info from local storage
    if (localStorage.getItem("userInfo")) {
      this.user.name = (JSON.parse(localStorage.getItem("userInfo"))[0].name).toUpperCase();
      let img = JSON.parse(localStorage.getItem("userInfo"))[0].image;
      
      // We check if the image is a valid URL
      if(this.checkURL (img)){
        this.user.image = img;
      } else{
        this.user.image = "src/assets/default_img.png";
      }  

      //console.log(this.user);
    } else {
      // If the user is not logged in, we redirect him to the login page
      this.$router.push("/login");
    }
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
        <img src="src\assets\logo_image.png" alt="logo" class="header-img" />
        <h2 class="title">OPEN EVENTS</h2>
      </div>

      <div id="user-photo">
        <RouterLink id="profile-btn" to="/profile">
          <h2 class="title">{{ user.name }}</h2>
        </RouterLink>
        <img
          v-bind:src="user.image"
          onerror="this.src = 'src/assets/default_img.png'"
          alt="user photo"
          class="header-img"
        />
      </div>
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

      <div class="request-container">
        <p id="name-request">Ángel García</p>
        <div id="answer-buttons">
          <button class="accept-button">Accept</button>
          <button class="reject-button">Reject</button>
        </div>
      </div>

      <div class="request-container">
        <p id="name-request">Pol Valero</p>
        <div id="answer-buttons">
          <button class="accept-button">Accept</button>
          <button class="reject-button">Reject</button>
        </div>
      </div>

      <div id="last-request" class="request-container">
        <p id="name-request">Daniel Amo</p>
        <div id="answer-buttons">
          <button class="accept-button">Accept</button>
          <button class="reject-button">Reject</button>
        </div>
      </div>
    </aside>
  </div>

  <footer>
    <h5 class="small-padding">Copyright <span> LaSalle 2022</span></h5>
  </footer>
</template>

<style scoped></style>
