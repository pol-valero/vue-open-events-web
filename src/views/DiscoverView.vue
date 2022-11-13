<template>
  <!-- Main content -->
  <section id="discover-users-list-main">
    <!-- Users list header -->
    <h1 id="users-list-header">Users</h1>
    <!-- Searchbar -->
    <section id="users-searchbar" class="searchbar">
      <article id="users-searchbar-field" class="searchbar-field">
        <form action="">
          <input
            id="users-searchbar-placeholder"
            class="searchbar-placeholder"
            type="text"
            placeholder="Search"
          />
        </form>
        <button class="filters-show-button">Filters</button>
      </article>
    </section>
    <!-- Filters selector -->
    <section id="users-filters-box" class="filters-box">
      <img
        src="../assets/filter-icon.svg"
        alt="Close filters"
        id="users-filters-close-button"
        class="filters-close-button"
      />
      <article class="filter">
        <p class="user-filter-text">Name</p>
      </article>
      <article class="filter">
        <p class="user-filter-text">Date</p>
      </article>
      <article class="filter">
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

/* Searchbar */
#users-searchbar-field {
  min-width: 100%;
}

/* Filters */
/* Will be hidden until "Filters" button is pressed
#users-filters-box {
  display: none;
}
*/

/* Users list */
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

/* Adapt to device */
@media (max-width: 768px) {
  #discover-users-list-main {
    padding-bottom: 40px;
    padding-right: 20px;
  }

  #users-searchbar-field {
    flex-wrap: wrap;
    margin-bottom: 0px;
  }

  #users-searchbar-field > form,
  button {
    margin-bottom: 10px;
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
