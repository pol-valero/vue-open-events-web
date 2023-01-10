<script>

export default {
  name: "EventDetailsView",
  data() {
    return {
      event: { 
        title: this.$root.$data.eventToDisplay.title,
        description: this.$root.$data.eventToDisplay.description,
        startDate: this.$root.$data.eventToDisplay.startDate,
        endDate: this.$root.$data.eventToDisplay.endDate,
        location: this.$root.$data.eventToDisplay.location,
        image: this.$root.$data.eventToDisplay.image,
        type: this.$root.$data.eventToDisplay.type,
        capacity: this.$root.$data.eventToDisplay.capacity,
        organizer: this.$root.$data.eventToDisplay.organizer
      },
      date: {
        day: '',
        month: '',
        year: '',
        hour: '',
        minute: '',
        endDay: '',
        endMonth: '',
        endYear: '',
        endHour: '',
        endMinute: ''
      
      }
    };
  },

  mounted() {
    // We hide the aside
    this.$root.$data.show.aside = false;

    // We set the background image
    document.getElementById('title-container').style.backgroundImage = "url('" + this.event.image + "')"

    // We change the date format so that we can display it more easily
    var startTime = new Date (this.$root.$data.eventToDisplay.startDate)
    this.date.day = startTime.getDate()
    this.date.month = startTime.getMonth() + 1
    this.date.year = startTime.getFullYear()
    this.date.hour = startTime.getHours()
    this.date.minute = startTime.getMinutes()

    // We change the date format so that we can display it more easily
    var endTime = new Date (this.$root.$data.eventToDisplay.endDate)
    this.date.endDay = endTime.getDate()
    this.date.endMonth = endTime.getMonth() + 1
    this.date.endYear = endTime.getFullYear()
    this.date.endHour = endTime.getHours()
    this.date.endMinute = endTime.getMinutes()

  },
  
  methods: {
  },
};
</script>

<template>
  <div id="event-details-main">
    <section id="title-container">
      <div id="text-title">
        <h2>{{this.event.title}}</h2>
      </div>

      <div id="share-button">
        <button class="primary-button">SHARE!</button>
      </div>
    </section>

    <section id="details-container">
      <div class="detail">
        <img src="../assets/calendar-img.png" class="users-list-item-picture" />
        <div class="detail-text">
          <h4>From {{this.date.day}}/{{this.date.month}}/{{this.date.year}} - {{ this.date.hour }}:{{ this.date.minute }}</h4>
          <p>to {{this.date.endDay}}/{{this.date.endMonth}}/{{this.date.endYear}} - {{ this.date.endHour }}:{{ this.date.endMinute }}</p>
        </div>
      </div>

      <div class="detail">
        <img src="../assets/location-img.png" class="users-list-item-picture" />
        <div class="detail-text">
          <h4>{{ this.event.location }}</h4>
        </div>
      </div>

      <div class="detail">
        <img src="../assets/user-img.png" class="users-list-item-picture" />
        <div class="detail-text">
          <h4>{{this.event.organizer}}</h4>
          <p>Organizer</p>
        </div>
        <button id="follow-button" class="secondary-button">Follow</button>
      </div>
    </section>

    <section id="event-description">
      <h4>About event</h4>
      <p>Event type: {{ this.event.type }}</p>
      <p>Capacity: {{ this.event.capacity }}</p>
      <p>{{ this.event.description }}</p>
    </section>

    <div class="event-details-bottom-buttons">
      <!-- One will be hidden with JS (edit only for event creator) -->
      <button class="primary-button">PARTICIPATE</button>
      <button class="primary-button" onclick="location.href='/editEvent';">
        EDIT
      </button>
    </div>
  </div>
</template>

<style scoped>
#event-details-main {
  width: 100%;
  height: 100%;
  flex-direction: column;
  display: flex;
}

#title-container {
  background-repeat: no-repeat;
  background-size: cover;
  height: 40%;
  min-height: 200px;
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 30px;
}

#text-title {
  padding-left: 40px;
  font-size: 16px;
  width: 100%;
}

#share-button {
  display: flex;
  flex-direction: row;
  justify-content: end;
  width: 70px;
  padding-right: 30px;
}

#share-button button {
  height: 50px;
  width: 120px;
  box-shadow: 4px 4px 4px rgba(0, 0, 0, 0.2);
}

#details-container {
  display: flex;
  height: fit-content;
  flex-flow: row wrap;
  justify-content: space-between;
  margin-left: 40px;
  margin-right: 20px;
  margin-top: 10px;
}

.detail {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin: 10px;
  flex-wrap: wrap;
}

.users-list-item-picture {
  width: 40px;
  height: 40px;
  border-radius: 12px;
}

.detail-text {
  margin-left: 10px;
}

.detail-text h4 {
  font-size: 16px;
  margin-bottom: 3px;
}

.detail-text text {
  font-size: 12px;
  margin-bottom: 3px;
}

#follow-button {
  height: 30px;
  width: 90px;
  font-size: 12px;
  margin-left: 50px;
  margin-top: 10px;
}

#event-description {
  display: flex;
  flex-direction: column;
  height: fit-content;
  margin-left: 50px;
  margin-right: 50px;
  margin-top: 20px;
  line-height: 150%;
}

#event-description p {
  margin-top: 10px;
  text-align: justify;
  font-size: 14px;
}

.event-details-bottom-buttons {
  margin-top: 40px;
  align-self: center;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.event-details-bottom-buttons button {
  height: 50px;
  width: 120px;
  font-size: 16px;
  margin: 0px 40px 30px 40px;
}

@media (min-width: 596px) {
  .users-list-item-picture {
    width: 70px;
    height: 70px;
  }

  .detail-text h4 {
    font-size: 22px;
  }

  .detail-text text {
    font-size: 15px;
  }

  #details-container {
    margin-left: 70px;
    margin-right: 70px;
    margin-top: 20px;
  }

  #text-title {
    padding-left: 80px;
    font-size: 20px;
  }

  #share-button {
    width: 100%;
    padding-right: 70px;
  }

  #event-description {
    margin-left: 80px;
    margin-right: 80px;
    margin-top: 40px;
    line-height: 200%;
  }

  #event-description p {
    font-size: default;
  }

  .event-details-bottom-buttons {
    margin-top: 60px;
  }

  .event-details-bottom-buttons button {
    height: 80px;
    width: 210px;
    border-radius: 20px;
    font-size: 22px;
    margin: 0px 10px 30px 10px;
  }

  #follow-button {
    margin-top: 0px;
  }
}
</style>
