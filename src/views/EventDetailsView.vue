<script>
import CommentItem from "../components/commentItem.vue";

export default {
  name: "EventDetailsView",
  components: {CommentItem},
  data() {
    return {
      event: { 
        title: 'Title',
        description: 'Description',
        startDate: '2023-06-22T08:22:00.000Z',
        endDate: '2023-06-23T10:45:00.000Z',
        location: 'Location name',
        image: 'src/assets/event-details-background.png',
        type: 'Type',
        capacity: 0,
        organizer: 'Firstname Lastname',
        organizer_id: null,
        id: this.$route.params.eventID
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
      
      },
      comments: [],
      isParticipating: true
    };
  },

  mounted() {
    // We hide the aside
    this.$root.$data.show.aside = false;

    this.getEvent();
    this.getAssistances();

    // We change the date format so that we can display it more easily
    var startTime = new Date (this.event.startDate)
    this.date.day = startTime.getDate()
    this.date.month = startTime.getMonth() + 1
    this.date.year = startTime.getFullYear()
    this.date.hour = startTime.getHours()
    this.date.minute = startTime.getMinutes()

    // We change the date format so that we can display it more easily
    var endTime = new Date (this.event.endDate)
    this.date.endDay = endTime.getDate()
    this.date.endMonth = endTime.getMonth() + 1
    this.date.endYear = endTime.getFullYear()
    this.date.endHour = endTime.getHours()
    this.date.endMinute = endTime.getMinutes()
  },
  
  methods: {
    participate() {
      const token = localStorage.getItem('token');

      fetch('http://puigmal.salle.url.edu/api/v2/events/' + this.event.id + '/assistances', {
          method: 'POST',
          headers:{
            'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
            'Content-Type': 'application/json'
          }
          })
          .then(res => res.json())
          .then(res => {
            let response = JSON.stringify(res);
            this.$router.push("/")
          });
    },

    getEvent() {
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/events/' + this.event.id;
      fetch(URL, {
        method: 'GET',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },     
      })
      .then(res => res.json())
      .then(res => {
        this.event.title = res[0].name;
        this.event.description = res[0].description;
        this.event.startDate = res[0].eventStart_date;
        this.event.endDate = res[0].eventStart_date;
        this.event.location = res[0].location;
        this.event.type = res[0].type;
        this.event.capacity = res[0].n_participators;
        this.event.organizer_id = res[0].owner_id;

        // We set the background image
        document.getElementById('title-container').style.backgroundImage = "url('" + res[0].image + "')";
        this.getUser();
      });
    },

    getAssistances() {
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/events/' + this.event.id + '/assistances';
      let localUserID = JSON.parse(localStorage.getItem("userInfo"))[0].id;

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
        let tmpBool = false;
        let tmpComments = [];

        if (response.length > 0) {
          // prepare comments and ratings
          tmpComments = res;
          tmpComments.forEach((comment) => {
            // check if user is participating
            if (comment.id == localUserID) {
              tmpBool = true;
            }
            // add to comments array if it has a rating or a commentary
            if ((comment.puntuation != null) || (comment.commentary != null)) {
              this.comments.push(comment);
            }
          });

          this.isParticipating = tmpBool;
        }
      });
    },

    getUser() {
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/users/' + this.event.organizer_id;
      fetch(URL, {
        method: 'GET',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },     
      })
      .then(res => res.json())
      .then(res=> {
        this.event.organizer = res[0].name;
      });
    },

    followUser() {
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/friends/' + this.event.organizer_id;

      // send friend request
      fetch(URL, {
        method: 'POST',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },
      })
      .then(alert("Friend request sent!"));
    },

    addComment() {
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/events/' + this.event.id + '/assistances';
      let commentary = document.getElementById("comment-form-text").value;
      let rating = document.getElementById("comment-form-rating").value;

      if ((rating != "") && (commentary == "")) {
        // send only rating
        fetch(URL, {
          method: 'PUT',
          headers:{
            'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            "puntuation": rating
          })
        });
      } else if ((rating == "") && (commentary != "")) {
        // send only commentary
        fetch(URL, {
          method: 'PUT',
          headers:{
            'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            "comentary": commentary
          })
        });
      } else if ((rating != "") && (commentary != "")) {
        // send both
        fetch(URL, {
          method: 'PUT',
          headers:{
            'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            "puntuation": rating,
            "comentary": commentary
          })
        });
      } else {
        // send nothing
        alert("You must write a comment or rate the event!");
      }

      this.clearForm();
    },

    clearForm() {
      document.getElementById("comment-form-text").value = "";
      document.getElementById("comment-form-rating").value = "";
    }
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
        <button v-on:click="followUser()" id="follow-button" class="secondary-button">Follow</button>
      </div>
    </section>

    <section id="event-description">
      <h4>About event</h4>
      <p>Event type: {{ this.event.type }}</p>
      <p>Capacity: {{ this.event.capacity }}</p>
      <p>{{ this.event.description }}</p>
    </section>

    <div class="event-details-bottom-buttons" v-if="!isParticipating">
      <button v-on:click="participate()" class="primary-button">PARTICIPATE</button>
    </div>

    <article id="event-comments">
      <!-- Show all comments and ratings -->
      <section id="event-comments-list">
        <h3>Comments</h3>
        <ul>
          <li v-for="comment in comments" v-bind:key="comment.id" class="comment-list-item">
            <CommentItem
              :name="comment.name"
              :lastname="comment.last_name"
              :comment="comment.comentary"
              :rating="comment.puntuation"
            />
          </li>
        </ul>
      </section>
      <!-- Add comment and rating -->
      <section id="event-comments-add-section">
        <h3>Add comment</h3>
        <form id="comment-form" action="">
          <textarea id="comment-form-text" class="field" cols="30" rows="10" placeholder="Write your comment here..."/>
          <div id="comment-form-box">
            <input type="number" id="comment-form-rating" class="field" min="0" max="10" placeholder="Rating (0-10)"/>
            <button v-on:click="addComment()" id="comment-form-submit-button" class="primary-button">COMMENT</button>
          </div>
        </form>
      </section>
    </article>
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
  margin: 20px 50px 40px 50px;
  line-height: 150%;
}

#event-description p {
  margin-top: 10px;
  text-align: justify;
  font-size: 14px;
}

.event-details-bottom-buttons {
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

#event-comments {
  display: flex;
  flex-direction: column;
  align-content: center;
  margin-left: 30px;
  margin-right: 30px;
  margin-bottom: 40px;
}

#event-comments-add-section {
  background: #f8f8f8;
  border-radius: 12px;
  padding: 15px;
  height: fit-content;
}

#comment-form {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-between;
}

#comment-form textarea {
  width: 92%;
}

#comment-form-box {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-between;
}

#comment-form-box input {
  height: max-content;
}

#comment-form-submit-button {
  height: 40px;
}

#event-comments-list {
  margin-bottom: 40px;
}

.comment-list-item {
  background: #fafafa;
  margin-top: 10px;
  padding: 15px;
  border-radius: 12px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1);
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
    margin: 40px 80px 50px 80px;
    line-height: 200%;
  }

  #event-description p {
    font-size: default;
  }

  .event-details-bottom-buttons {
    margin-top: 0px;
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

  #event-comments {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-left: 80px;
    margin-right: 80px;
    margin-bottom: 40px;
  }

  #event-comments-add-section {
    width: 50%;
  }

  #comment-form {
    flex-direction: row;
  }

  #comment-form textarea {
    width: 50%;
  }

  #comment-form-box {
    width: 40%;
  }

  #event-comments-list {
    width: 30%;
    margin-bottom: 0px;
  }
}
</style>
