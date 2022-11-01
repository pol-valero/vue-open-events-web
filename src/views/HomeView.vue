<template>
  <section id="home-events-list-section">
    <!-- Events header -->
    <h1 id="events-list-header">Events</h1>
    <!-- Searchbar -->
    <section id="events-searchbar">
      <article id="events-searchbar-field">
        <form action="">
          <input
            id="events-searchbar-placeholder"
            type="text"
            placeholder="Search"
          />
        </form>
        <button>Filters</button>
      </article>
      <!-- Create event button -->
      <button id="create-event-button">Create event</button>
    </section>
    <!-- Filters selector -->
    <section id="events-filters-box">
      <img
        src="../assets/filter-icon.svg"
        alt="Close filters"
        id="events-filters-close-button"
      />
      <article class="event-filter">
        <p class="event-filter-text">Name</p>
      </article>
      <article class="event-filter">
        <p class="event-filter-text">Date</p>
      </article>
      <article class="event-filter">
        <p class="event-filter-text">Location</p>
      </article>
    </section>
    <!-- Events list -->
    <section id="events-list-section">
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
  min-height: 100%;
  margin: 20px;
  margin-bottom: 40px;
}

#events-searchbar {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  width: inherit;
  margin-top: 10px;
  margin-bottom: 10px;
}

#events-searchbar-field {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  min-width: 80%;
  margin-right: 40px;
  margin-bottom: 10px;
}

#events-searchbar-field > form {
  min-width: 85%;
  margin-right: 40px;
}

#events-searchbar-placeholder {
  padding: 5px;
  border: solid #e3e3e3 2px;
  border-radius: 10px;
  width: 100%;
}

#events-searchbar-field > button {
  background-color: black;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 5px;
}

#events-searchbar-field > button:hover {
  background-color: #5a5a5a;
}

#create-event-button {
  padding: 5px;
}

/* Will be hidden until "Filters" button is pressed */
#events-filters-box {
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

#events-filters-close-button {
  width: 10%;
  height: auto;
  margin-right: 20px;
}

.event-filter {
  background-color: white;
  margin-top: 10px;
  margin-bottom: 10px;
  padding: 9px;
  border-radius: 15px;
  width: fit-content;
}

.event-filter ~ .event-filter {
  margin-left: 10px;
}

.event-filter:hover {
  background-color: #bce7c8;
}

.event-filter > p {
  font-size: 1.6vmin;
}

#events-list-section {
  /* Configure flex layout */
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.events-list-item {
  background: #fafafa;
  margin-top: 10px;
  width: 45%;
  height: auto;
  padding: 10px;
  display: flex;
  flex-direction: row;
  align-items: center;
  border-radius: 12px;
  box-shadow: 5px 5px 5px #ddd;
}

.events-list-item-picture {
  max-width: 15%;
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
  /* Style of dates in events preview */
  font-size: 1.7vmin;
}

.events-list-item-title {
  /* Style of title in events preview */
  font-size: 2vmin;
  margin-top: 10px;
}

.events-list-item-location {
  /* Style of location in events preview */
  align-self: flex-end;
  margin-top: 10px;
  font-size: 1.9vmin;
}

@media (max-width: 768px) {
  #home-events-list-section {
    margin: 20px;
  }

  #events-filters-box {
    max-width: 70%;
  }

  #events-filters-close-button {
    width: 12%;
    height: auto;
    margin-right: 30px;
  }

  .event-filter ~ .event-filter {
    margin-left: 20px;
  }

  .event-filter > p {
    font-size: 2vmin;
  }

  #events-list-section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .events-list-item {
    width: 85%;
  }

  .events-list-item-date {
    font-size: 2vmin;
  }

  .events-list-item-title {
    font-size: 2.8vmin;
  }

  .events-list-item-location {
    font-size: 2.2vmin;
  }
}
</style>
