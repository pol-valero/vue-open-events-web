<template>
  <section id="home-events-list-section">
    <!-- Events header -->
    <h1 id="events-list-header">Events</h1>
    <!-- Searchbar -->
    <section id="events-searchbar" class="searchbar">
      <article id="events-searchbar-field" class="searchbar-field">
        <form action="">
          <input
            id="events-searchbar-placeholder"
            class="searchbar-placeholder"
            type="text"
            placeholder="Search"
          />
        </form>
        <button class="filters-show-button">Filters</button>
      </article>
      <!-- Create event button -->
      <a href="/createEvent">
        <button id="create-event-button" type="button">Create event</button>
      </a>
    </section>
    <!-- Filters selector -->
    <section id="events-filters-box" class="filters-box">
      <img
        src="../assets/filter-icon.svg"
        alt="Close filters"
        id="events-filters-close-button"
        class="filters-close-button"
      />
      <article class="filter">
        <p class="event-filter-text">Name</p>
      </article>
      <article class="filter">
        <p class="event-filter-text">Date</p>
      </article>
      <article class="filter">
        <p class="event-filter-text">Location</p>
      </article>
    </section>
    <!-- Events list -->
    <section id="events-list-section">
      <!-- Temporary link to EventDetailsView -->
      <RouterLink id="tmp-events-item-link" to="/eventDetails">
        <article class="events-list-item">
          <img
            src="../assets/default_img.png"
            alt="Picture of the event"
            class="events-list-item-picture"
          />
          <div class="event-preview-content">
            <p class="events-list-item-date">20/11/2022 - 15:08</p>
            <h2 class="events-list-item-title">House BBQ</h2>
            <p class="events-list-item-location">Alabama</p>
          </div>
        </article>
      </RouterLink>
      <article class="events-list-item">
        <img
          src="../assets/default_img.png"
          alt="Picture of the event"
          class="events-list-item-picture"
        />
        <div class="event-preview-content">
          <p class="events-list-item-date">01/12/2022 - 11:20</p>
          <h2 class="events-list-item-title">Mushroom harvesting</h2>
          <p class="events-list-item-location">Hawaii</p>
        </div>
      </article>
      <article class="events-list-item">
        <img
          src="../assets/default_img.png"
          alt="Picture of the event"
          class="events-list-item-picture"
        />
        <div class="event-preview-content">
          <p class="events-list-item-date">27/11/2022 - 20:00</p>
          <h2 class="events-list-item-title">Ping pong tournament</h2>
          <p class="events-list-item-location">Owensboro</p>
        </div>
      </article>
      <article class="events-list-item">
        <img
          src="../assets/default_img.png"
          alt="Picture of the event"
          class="events-list-item-picture"
        />
        <div class="event-preview-content">
          <p class="events-list-item-date">13/12/2022 - 9:45</p>
          <h2 class="events-list-item-title">LOTR marathon</h2>
          <p class="events-list-item-location">Milan</p>
        </div>
      </article>
      <article class="events-list-item">
        <img
          src="../assets/default_img.png"
          alt="Picture of the event"
          class="events-list-item-picture"
        />
        <div class="event-preview-content">
          <p class="events-list-item-date">11/02/2023 - 14:00</p>
          <h2 class="events-list-item-title">Private car race</h2>
          <p class="events-list-item-location">Barcelona</p>
        </div>
      </article>
      <article class="events-list-item">
        <img
          src="../assets/default_img.png"
          alt="Picture of the event"
          class="events-list-item-picture"
        />
        <div class="event-preview-content">
          <p class="events-list-item-date">01/01/2023 - 22:55</p>
          <h2 class="events-list-item-title">New year party #2</h2>
          <p class="events-list-item-location">Tokyo</p>
        </div>
      </article>
      <article class="events-list-item">
        <img
          src="../assets/default_img.png"
          alt="Picture of the event"
          class="events-list-item-picture"
        />
        <div class="event-preview-content">
          <p class="events-list-item-date">10/11/2022 - 18:15</p>
          <h2 class="events-list-item-title">Interdimensional cable</h2>
          <p class="events-list-item-location">C-137</p>
        </div>
      </article>
    </section>
  </section>
</template>

<style scoped>
#home-events-list-section {
  padding: 20px 20px 40px 20px;
}

/* Searchbar */
#events-searchbar-field {
  max-width: 100%;
  width: 100%;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-right: 0px;
}

#events-searchbar-field > form {
  min-width: 65%;
  margin-right: 10px;
}

/* Create event */
#create-event-button {
  padding: 8px;
  margin-bottom: 10px;
  background-color: rgb(119, 34, 255);
  color: #fff;
  border-radius: 10px;
  border: none;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1);
}

#create-event-button:hover {
  box-shadow: inset 2px 2px 5px rgba(0, 0, 0, 0.5);
}

/* Filters */
/* Will be hidden until "Filters" button is pressed
#events-filters-box {
  display: none;
}
*/

/* Events list */
#events-list-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-wrap: wrap;
}

/* Temporary style for link to EventDetailsView (will be done with JS later) */
#tmp-events-item-link {
  width: 85%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-decoration: none;
}

#tmp-events-item-link > .events-list-item {
  width: 100%;
}

#tmp-events-item-link p,
h2 {
  color: #000;
}
/* End of temporary style */

.events-list-item {
  background: #fafafa;
  margin-top: 10px;
  width: 85%;
  height: auto;
  padding: 10px;
  display: flex;
  flex-direction: row;
  align-items: center;
  border-radius: 12px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1);
}

.events-list-item:hover {
  cursor: pointer;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.3);
}

.events-list-item-picture {
  max-width: 25%;
  width: auto;
  height: fit-content;
  border-radius: 12px;
}

.event-preview-content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 10px;
  width: 100%;
}

.events-list-item-date {
  font-size: 2.7vmin;
  cursor: pointer;
}

.events-list-item-title {
  font-size: 3.4vmin;
  margin-top: 10px;
  cursor: pointer;
}

.events-list-item-location {
  align-self: flex-end;
  margin-top: 10px;
  font-size: 2.9vmin;
  cursor: pointer;
}

/* Adapt to device */
@media (min-width: 768px) {
  #home-events-list-section {
    padding-bottom: 50px;
    padding-right: 30px;
  }

  #events-searchbar-field {
    flex-wrap: nowrap;
    justify-content: flex-start;
    margin-right: 40px;
    min-width: 80%;
  }

  #events-searchbar-field > form {
    min-width: 85%;
    margin-right: 40px;
  }

  /*#events-searchbar-placeholder {
    max-width: 100%;
    width: 100%;
  }*/

  #events-list-section {
    flex-direction: row;
    justify-content: space-between;
  }

  /* Temporary style for link to EventDetailsView (will be done with JS later) */
  #tmp-events-item-link {
    display: block;
    width: 45%;
  }
  /* End of temporary style */

  .events-list-item {
    width: 45%;
  }

  .events-list-item-picture {
    max-width: 15%;
  }

  .events-list-item-date {
    font-size: 1.7vmin;
  }

  .events-list-item-title {
    font-size: 2vmin;
  }

  .events-list-item-location {
    font-size: 1.9vmin;
  }
}
</style>
