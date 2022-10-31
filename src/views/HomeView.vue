<template>
  <section id="homeEventsListSection">
    <!-- Events header -->
    <h1 id="eventsListHeader">Events</h1>
    <!-- Searchbar -->
    <section id="eventsSearchbar">
      <article id="eventsSearchbarField">
        <form action="">
          <input
            id="eventsSearchbarPlaceholder"
            type="text"
            placeholder="Search"
          />
        </form>
        <button>Filters</button>
      </article>
      <!-- Create event button -->
      <button id="createEventButton">Create event</button>
    </section>
    <!-- Events list -->
    <section id="eventsListSection">
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" class="eventsListItemPicture" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 1</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 2</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 3</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 4</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 5</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 6</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
      <article class="eventsListItem">
        <img src="" alt="Picture of the event" />
        <div class="eventPreviewContent">
          <p class="eventsListItemDate">DD/MM/YYYY - HH:MM</p>
          <h2 class="eventsListItemTitle">Event 7</h2>
          <p class="eventsListItemLocation">Location</p>
        </div>
      </article>
    </section>
  </section>
</template>

<style scoped>
#homeEventsListSection {
  min-height: 100%;
  margin: 20px;
}

#eventsSearchbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: pink;
  width: inherit;
}

#eventsSearchbarField {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

#eventsSearchbarField > button {
  background: black;
  color: white;
  border: none;
  padding: 5px;
}

#eventsListSection {
  /* Configure flex layout */
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.eventsListItem {
  background: lightblue;
  margin-top: 10px;
  min-width: 47%;
  padding: 5px;
  display: flex;
  flex-direction: row;
}

.eventsListItemPicture {
  max-width: 15%;
  width: auto;
  height: auto;
}

.eventPreviewContent {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-left: 10px;
  width: 100%;
}

.eventsListItemDate {
  /* Style of dates in events preview */
  font-size: 0.8em;
}

.eventsListItemTitle {
  /* Style of title in events preview */
  font-size: 1.2rem;
  /*font-weight: bold;*/
}

.eventsListItemLocation {
  /* Style of location in events preview */
  align-self: flex-end;
}

@media (max-width: 768px) {
  #homeEventsListSection {
    margin: 20px;
  }
  #eventsListSection {
    display: block;
  }
}
</style>
