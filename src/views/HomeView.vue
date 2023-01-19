<script>
  export default {
    name: "HomeView",
    data() {
      return {
        events: [],
      };
    },

    methods: {
      checkURL(url) {
        return(url.match(/\.(jpeg|jpg|gif|png)$/) != null);
      },

      searchEvents() {
        const token = localStorage.getItem('token');
        let location = document.getElementById("events-location-searchbar-placeholder").value;
        let name = document.getElementById("events-name-searchbar-placeholder").value;
        let date = document.getElementById("events-date-searchbar-placeholder").value;
        let URL = 'http://puigmal.salle.url.edu/api/v2/events/search?';
        
        // prepare URL for API request
        if (location != "") {
          // search by location
          URL += 'location=' + location;
          if (name != "") {
            // search by location and name
            URL += '&keyword=' + name;
            if (date != "") {
              // search by location and name and date
              URL += '&date=' + date;
            }
          } else if (date != "") {
            // search by location and date
            URL += '&date=' + date;
          }
        } else if (name != "") {
          // search by name
          URL += 'keyword=' + name;
          if (date != "") {
            // search by name and date
            URL += '&date=' + date;
          }
        } else if (date != "") {
          // search by date
          URL += 'date=' + date;
        } else {
          // no search
          URL = 'http://puigmal.salle.url.edu/api/v2/events/best';
        }

        fetch(URL, {
          method: 'GET',
          headers:{
            'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
            'Content-Type': 'application/json',
          },
        })
        .then(res => res.json())
        .then(res => {
          let response = JSON.stringify(res);
          if(response.length > 0) {
            this.events = res;
            res.map((event) => {
              // remove time from date
              if (event.eventStart_date != null) {
                event.eventStart_date = event.eventStart_date.split('T')[0];
              }
              // get the image of the event
              if(this.checkURL(event.image)){
                event.image = event.image;
              } else{
                event.image = "/src/assets/default_img.png";
              }  
            });
          }
        });
      }
    },

    mounted() {
      // We show the aside and the header
      this.$root.$data.show.aside = true;
      this.$root.$data.show.header = true;
      this.searchEvents();
    },
  };

</script>

<template>
  <section id="home-events-list-section">
    <!-- Events header -->
    <h1 id="events-list-header">Events</h1>
    <!-- Searchbar -->
    <section id="events-searchbar" class="searchbar">
      <!-- Name searchbar -->
      <article id="events-name-searchbar" class="searchbar-field events-searchbar-field">
        <form action="">
          <input
            v-on:input="searchEvents()"
            id="events-name-searchbar-placeholder"
            class="searchbar-placeholder events-searchbar-placeholder"
            type="text"
            placeholder="Name"
          />
        </form>
      </article>
      <!-- Location searchbar -->
      <article id="events-location-searchbar" class="searchbar-field events-searchbar-field">
        <form action="">
          <input
            v-on:input="searchEvents()"
            id="events-location-searchbar-placeholder"
            class="searchbar-placeholder events-searchbar-placeholder"
            type="text"
            placeholder="Location"
          />
        </form>
      </article>
      <!-- Date searchbar -->
      <article id="events-date-searchbar" class="searchbar-field events-searchbar-field">
        <form action="">
          <input
            v-on:input="searchEvents()"
            id="events-date-searchbar-placeholder"
            class="searchbar-placeholder events-searchbar-placeholder"
            type="date"
            placeholder="Date"
          />
        </form>
      </article>
      <!-- Create event button -->
      <a href="/createEvent">
        <button id="create-event-button" type="button">Create event</button>
      </a>
    </section>
    <!-- Events list -->
    <section id="events-list-section">
      <ul>
        <li v-for="event in events" v-bind:key="event.id" v-on:click="this.$router.push('/eventDetails/' + event.id)">
          <article class="events-list-item">
            <img
              v-bind:src="event.image"
              onerror="this.src = '/src/assets/default_img.png'"
              alt="Picture of the event"
              class="events-list-item-picture"
            />
            <div class="event-preview-content">
              <p class="events-list-item-date">{{event.eventStart_date}}</p>
              <h2 class="events-list-item-title">{{event.name}}</h2>
              <p class="events-list-item-location">{{event.location}}</p>
            </div>
          </article>
        </li>
      </ul>
    </section>
  </section>
</template>

<style scoped>
#home-events-list-section {
  padding: 20px 20px 40px 20px;
}

/* Searchbar */
.events-searchbar-field {
  max-width: 100%;
  width: 100%;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-right: 0px;
}

.events-searchbar-field > form {
  min-width: 100%;
}

.events-searchbar-placeholder {
  width: 95%;
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

/* Events list */
#events-list-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-wrap: wrap;
}

ul {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  list-style-type: none;
  padding: 0;
  margin: 0;
  width: 100%;
  align-content: center;
}

li {
  width: 85%;
}

.events-list-item {
  background: #fafafa;
  margin-top: 10px;
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

  .events-searchbar-field {
    flex-wrap: nowrap;
    justify-content: flex-start;
    width: auto;
    min-width: 25%;
  }

  .events-searchbar-field > form {
    min-width: 90%;
  }

  .events-searchbar-placeholder {
    width: 100%;
  }

  #events-list-section {
    flex-direction: row;
    justify-content: space-between;
  }

  ul {
    flex-direction: row;
    justify-content: space-between;
  }

  li {
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
