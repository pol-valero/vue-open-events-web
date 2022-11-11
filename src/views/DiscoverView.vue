<template>
  <!-- Main content -->
  <section id="discover-users-list-main">
    <!-- Users list header -->
    <h1 id="users-list-header">Users</h1>
    <!-- Searchbar -->
    <section id="users-searchbar">
      <article id="users-searchbar-field">
        <form action="">
          <input
            id="users-searchbar-placeholder"
            type="text"
            placeholder="Search"
          />
        </form>
        <button>Filters</button>
      </article>
    </section>
    <!-- Filters selector -->
    <section id="users-filters-box">
      <img
        src="../assets/filter-icon.svg"
        alt="Close filters"
        id="users-filters-close-button"
      />
      <article class="user-filter">
        <p class="user-filter-text">Name</p>
      </article>
      <article class="user-filter">
        <p class="user-filter-text">Date</p>
      </article>
      <article class="user-filter">
        <p class="user-filter-text">Location</p>
      </article>
    </section>
    <!-- Users list -->
    <section id="users-list-section">
      <RouterLink id="tmp-users-item-link" to="/profile">
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      </RouterLink>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 2</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 3</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 4</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 5</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 6</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 7</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 8</h2>
      </article>
    </section>
  </section>
</template>

<style scoped>

#discover-users-list-main {
  padding: 20px 30px 50px 20px;
}

#users-searchbar {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  width: inherit;
  margin-top: 10px;
}

#users-searchbar-field {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  min-width: 100%;
  margin-right: 40px;
  margin-bottom: 10px;
}

#users-searchbar-field > form {
  min-width: 85%;
  margin-right: 40px;
}

#users-searchbar-placeholder {
  padding: 5px;
  border: solid #e3e3e3 2px;
  border-radius: 10px;
  width: 100%;
}

#users-searchbar-field > button {
  background-color: black;
  color: white;
  border: none;
  border-radius: 10px;
  padding: 7px;
}

#users-searchbar-field > button:hover {
  background-color: #5a5a5a;
  transition: 0.4s;
}

/* Will be hidden until "Filters" button is pressed */
#users-filters-box {
  background-color: black;
  margin-bottom: 10px;
  padding-left: 15px;
  padding-right: 15px;
  padding-top: 5px;
  padding-bottom: 5px;
  border-radius: 15px;
  width: fit-content;
  max-width: 40%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
}

#users-filters-close-button {
  width: 10%;
  height: fit-content;
  margin-right: 20px;
  align-self: center;
  padding: 2px;
}

#users-filters-close-button:hover {
  cursor: pointer;
  box-shadow: inset 0px 2px 5px rgba(255, 255, 255, 0.8);
  background-color: #000;
}

.user-filter {
  background-color: white;
  margin-top: 10px;
  margin-bottom: 10px;
  padding: 9px;
  border-radius: 15px;
  width: fit-content;
}

.user-filter ~ .user-filter {
  margin-left: 10px;
}

.user-filter:hover {
  cursor: pointer;
  background-color: #bce7c8;
  transition: 0.4s;
}

.user-filter > p {
  font-size: 1.6vmin;
}

#users-list-section {
  /* Configure flex layout */
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

/* Temporary style for ProfileView temporary link (will be done with JS later) */
#tmp-users-item-link {
  width: 45%;
  text-decoration: none;
}

#tmp-users-item-link > .users-list-item {
  width: 100%;
  color: #000;
}
/* End of temporary style */

.users-list-item {
  background: #fafafa;
  margin-top: 20px;
  margin-right: 10px;
  width: 45%;
  padding: 10px;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  border-radius: 12px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1);
}

.users-list-item:hover {
  cursor: pointer;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.3);
}

.users-list-item-picture {
  max-width: 15%;
  width: auto;
  height: fit-content;
  border-radius: 12px;
  margin-right: 15px;
}

.users-list-item-picture:empty {
  font-size: 1.2vmin;
}

.users-list-item-title {
  font-size: 2vmin;
}

@media (max-width: 768px) {
  #discover-users-list-main {
    padding-bottom: 40px;
    padding-right: 20px;
  }

  #users-searchbar-field {
    flex-wrap: wrap;
    margin-bottom: 0px;
  }

  #users-searchbar-field > form, button {
    margin-bottom: 10px;
  }

  #users-filters-box {
    max-width: 88%;
  }

  #users-filters-close-button {
    width: 12%;
    height: auto;
    margin-right: 15px;
  }

  .user-filter {
    margin-top: 6px;
    margin-bottom: 6px;
  }

  .user-filter ~ .user-filter {
    margin-left: 10px;
  }

  .user-filter > p {
    font-size: 3.3vmin;
  }

  #users-list-section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  /* Temporary style for ProfileView temporary link (will be done with JS later) */
  #tmp-users-item-link {
    width: 85%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  /* End of temporary style */

  .users-list-item {
    width: 85%;
  }

  .users-list-item-title {
    font-size: 3.5vmin;
  }
}
</style>
