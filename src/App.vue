<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <div id="top-header">
      <div id="title-logo">
        <img src="src\assets\logo_image.png" alt="logo" class="header-img" />
        <h2 class="title">OPEN EVENTS</h2>
      </div>

      <div id="user-photo">
        <RouterLink id="profile-btn" to="/profile">
          <h2 class="title">USER</h2>
        </RouterLink>
        <img
          src="src\assets\default_img.png"
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

    <aside>
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
