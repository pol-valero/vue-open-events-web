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
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
      <article class="users-list-item">
        <img
          src="../assets/default_img.png"
          alt="User's profile picture"
          class="users-list-item-picture"
        />
        <h2 class="users-list-item-title">User 1</h2>
      </article>
    </section>
  </section>
</template>

<style scoped>

#discover-users-list-main {
  min-height: 100%;
  margin: 20px;
  margin-bottom: 40px;
}

#users-searchbar {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  width: inherit;
  margin-top: 10px;
  margin-bottom: 10px;
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
  border-radius: 5px;
  padding: 5px;
}

#users-searchbar-field > button:hover {
  background-color: #5a5a5a;
  transition: 0.4s;
}

/* Will be hidden until "Filters" button is pressed */
#users-filters-box {
  background-color: black;
  margin-top: 10px;
  margin-bottom: 20px;
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
  height: auto;
  margin-right: 20px;
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

.users-list-item {
  background: #fafafa;
  margin-top: 10px;
  width: 30%;
  padding: 10px;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  border-radius: 12px;
  box-shadow: 5px 5px 5px #ddd;
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
  margin-top: 10px;
}

@media (max-width: 768px) {
  #discover-users-list-main {
    margin: 20px;
  }

  #users-filters-box {
    max-width: 70%;
  }

  #users-filters-close-button {
    width: 12%;
    height: auto;
    margin-right: 30px;
  }

  .user-filter ~ .user-filter {
    margin-left: 20px;
  }

  .user-filter > p {
    font-size: 2vmin;
  }

  #users-list-section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .users-list-item {
    width: 85%;
  }
  .users-list-item-title {
    font-size: 2.8vmin;
  }
}
</style>
