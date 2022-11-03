<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <body>
    <header>
      <div id="top-header">
        <div id="title-logo">
          <img
            src="src\assets\logo_image.png"
            alt="logo"
          />
          <h2 class="title">OPEN EVENTS</h2>
        </div>

        <div id="user-photo">
          <div id="user-and-profile">
            <h2 class="title">USER</h2>
            <a id="profile-btn" class="std-padding" href="/profile">Profile</a>
          </div>
          <img
            src="src\assets\default_img.png"
            alt="user photo"
          />
        </div>
      </div>

      <div id="bot-header">
        <input type="checkbox" id="check-box" />

        <nav id="barra-nav">
          <a id="barra-nav-home" class="std-padding" href="/">HOME</a>
          <a id="barra-nav-discover" class="std-padding" href="/discover">DISCOVER</a>
          <a id="barra-nav-friends" class="std-padding" href="/chat">FRIENDS</a>
          <label for="check-box" id="hide-menu">&#215</label>
        </nav>
        <label for="check-box" id="show-menu">&#8801</label>
      </div>
    </header>

  <div id="center-screen">
    <main>
      <!-- HERE ALL THE MAIN CODDE -->
      <RouterView />
    </main>

    <aside>
      <h3 class="title">REQUESTS</h3>

      <div class="request-container">
        <p id="name-request">Ángel García</p>
        <div id="answer-buttons">
          <button class="small-button">Accept</button>
          <button class="small-button">Reject</button>
        </div>
      </div>

      <div class="request-container">
        <p id="name-request">Pol Valero</p>
        <div id="answer-buttons">
          <button class="small-button">Accept</button>
          <button class="small-button">Reject</button>
        </div>
      </div>

      <div id="last-request" class="request-container">
        <p id="name-request">Daniel Amo</p>
        <div id="answer-buttons">
          <button class="small-button">Accept</button>
          <button class="small-button">Reject</button>
        </div>
      </div>
    </aside>
  </div>

  <footer>
    <h5 class="small-padding">Copyright &copy LaSalle 2022</h5>
  </footer>
  </body>
</template>

<style scoped></style>
