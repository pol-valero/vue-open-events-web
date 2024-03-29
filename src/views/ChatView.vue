<script>
// We define the data that we will use to show the chat
export default {
  name: "ChatView",
  data() {
    return {
      userID: -1,
      userFriends: [],
      userChatting: {
        id: "",
        name: "",
        surname: "",
        image: "",
      },
      messages: [],
    };
  },
  //created lifecycle method
  created() {
    //Getting the user's ID
    this.userID = JSON.parse(localStorage.getItem("userInfo"))[0].id;
    //Getting the user's token
    const token = localStorage.getItem("token");
    //Making a request to show the user's friends list
    fetch("http://puigmal.salle.url.edu/api/v2/friends", {
      method: "GET",
      headers: {
        Authorization: "Bearer " + JSON.parse(token).accessToken,
        "Content-Type": "application/json",
      },
    })
      .then((res) => res.json())
      .then((res) => {
        let response = JSON.stringify(res);
        // We check if the user has friends
        if (response.length > 0) {
          this.userFriends = res;
          res.map((friend) => {
            // We check if the friend has a valid profile picture
            if (!this.checkURL(friend.image)) {
              friend.image = "src/assets/default_img.png";
            }
          });

          // We show the first friend's chat by default
          this.showChat(this.userFriends[0]);
        } else {
          alert("You have no friends yet, try to add some!");
        }
      });

    // We hide the aside of the app.vue
    this.$root.$data.show.aside = false;
  },

  methods: {
    showChat(friendChatting) {
      // We first change the user that we are chatting with
      this.userChatting.id = friendChatting.id;
      this.userChatting.name = friendChatting.name;
      this.userChatting.surname = friendChatting.last_name;
      // We check if the friend has a valid profile picture
      if (this.checkURL(friendChatting.image)) {
        this.userChatting.image = friendChatting.image;
      } else {
        this.userChatting.image = "src/assets/default_img.png";
      }

      // Then we make a request to get the messages between the two users
      const token = localStorage.getItem("token");
      const URL =
        "http://puigmal.salle.url.edu/api/v2/messages/" + friendChatting.id;
      fetch(URL, {
        method: "GET",
        headers: {
          Authorization: "Bearer " + JSON.parse(token).accessToken,
          "Content-Type": "application/json",
        },
      })
        .then((res) => res.json())
        .then((res) => {
          let response = JSON.stringify(res);
          // We check if the user has messages with the friend
          if (response.length > 0) {
            this.messages = res;
          } else {
            alert("You have no messages with this user yet!");
          }
        });
    },

    // We send the message when the input is filled and the button is clicked
    sendMessage() {
      const messageContent = document.getElementById("message-send").value;
      // We check if the message is empty
      if (messageContent.length == 0) {
        alert("You can't send an empty message!");
        return;
      }

      // Then we make a request to send the message
      const token = localStorage.getItem("token");
      const URL = "http://puigmal.salle.url.edu/api/v2/messages";
      fetch(URL, {
        method: "POST",
        headers: {
          Authorization: "Bearer " + JSON.parse(token).accessToken,
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          content: messageContent,
          user_id_send: this.userID,
          user_id_recived: this.userChatting.id,
        }),
      })
        // We add the message to the messages array or we show an error if the message couldn't be sent
        .then((res) => res.json())
        .then((res) => {
          this.messages.push(res);
        })
        .catch(() => alert("The message couldn't be sent! Try again later!"));

      // We clear the input
      document.getElementById("message-send").value = "";
    },

    // We check if the URL is valid
    checkURL(url) {
      return url.match(/\.(jpeg|jpg|gif|png)$/) != null;
    },
  },
};
</script>

<template>
  <div id="chat-main">
    <section id="container-chat-person">
      <h4 id="chats-title">Friends</h4>
      <ul v-for="friend in userFriends" v-bind:key="friend.id">
        <li>
          <button v-on:click="showChat(friend)" class="btn-chat">
            <div class="chat-person">
              <img
                class="little-img"
                v-bind:src="friend.image"
                onerror="this.src = 'src/assets/default_img.png'"
                alt="friend image"
              />
              <h5 class="name-padding">
                {{ friend.name + " " + friend.last_name }}
              </h5>
            </div>
          </button>
        </li>
      </ul>
    </section>

    <section id="container-chat-interactive">
      <div id="container-chat-person-selected">
        <img
          class="little-img"
          v-bind:src="userChatting.image"
          onerror="this.src = 'src/assets/default_img.png'"
          alt="friend image"
        />
        <h5
          id="name-big-padding"
          v-on:click="this.$router.push('/profile/' + userChatting.id)"
        >
          {{ userChatting.name + " " + userChatting.surname }}
        </h5>
      </div>

      <div class="scroller">
        <div
          v-for="message in messages"
          v-bind:key="message.id"
          id="container-full-chat"
        >
          <div v-if="message.user_id_send == userID" class="my-message">
            <h4 class="message">{{ message.content }}</h4>
            <h6>
              {{
                message.timeStamp.split("T")[0] +
                " / " +
                message.timeStamp.split("T")[1].substring(0, 5)
              }}
            </h6>
          </div>

          <div v-else class="other-message">
            <div>
              <h4 class="message">{{ message.content }}</h4>
              <h6>
                {{
                  message.timeStamp.split("T")[0] +
                  " / " +
                  message.timeStamp.split("T")[1].substring(0, 5)
                }}
              </h6>
            </div>
          </div>
        </div>
      </div>

      <div id="container-chat-input">
        <input id="message-send" type="text" placeholder="Message" />
        <button v-on:click="sendMessage()" class="btn-chat">
          <i class="material-icons">send</i>
        </button>
      </div>
    </section>
  </div>
</template>

<style scoped>
/* People */
.little-img {
  width: 40px;
  height: 40px;
}

#chat-main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

#container-chat-person {
  background-color: #f8f8f8;
  padding: 15px;
  display: flex;
  flex-direction: column;
  box-shadow: 2px 0px 5px 0px rgba(0, 0, 0, 0.1);
  z-index: 1;
}

.chat-person {
  padding-top: 8px;
  padding-bottom: 8px;
  display: flex;
  flex-direction: row;
  align-items: center;
  border-bottom: #ddd solid 2px;
}

#chats-title {
  margin-bottom: 10px;
  font-size: 20px;
}

.name-padding {
  padding-left: 7px;
  font-size: 11px;
}

.btn-chat {
  border: none;
  background: none;
}

.btn-chat:hover {
  color: #7722ff;
  transition: 0.2s;
  cursor: pointer;
}

.btn-chat h5 {
  cursor: pointer;
}

/* Messages */
#container-chat-interactive {
  background-color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
}

#container-chat-person-selected {
  background-color: #eee;
  padding: 10px 15px;
  display: flex;
  flex-direction: row;
  align-items: center;
}

/* Current chat header */
#friend-profile-btn {
  color: #000;
  text-decoration: none;
}

#name-big-padding {
  padding-left: 10px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
}

#name-big-padding:hover {
  color: #7722ff;
}

#container-full-chat {
  margin: 10px;
  display: flex;
  flex-direction: column;
}

.my-message h4 {
  border-radius: 30px;
  padding: 12px;
  background-color: #7722ff;
  margin-bottom: 5px;
  color: #fff;
}

.my-message h6 {
  padding-right: 10px;
}

.my-message {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-end;
  flex-wrap: wrap;
  margin-bottom: 15px;
}

.other-message h4 {
  border-radius: 30px;
  padding: 12px;
  background-color: #eee;
  margin-bottom: 4px;
}

.other-message h6 {
  display: flex;
  justify-content: flex-end;
  padding-right: 10px;
}

.other-message {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex-wrap: wrap;
  margin-bottom: 15px;
}

#container-chat-input {
  background: #eeeeff;
  padding: 10px;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

input {
  width: 80%;
  padding: 5px;
  margin-right: 5px;
  border: solid #e3e3e3 2px;
  border-radius: 10px;
}

.message {
  font-size: 13px;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.scroller {
  height: 550px;
  overflow-y: scroll;
  scrollbar-color: rebeccapurple green;
  scrollbar-width: thin;
}

/*MEDIA QUERIES*/
@media (min-width: 768px) {
  #chat-main {
    flex-direction: row;
  }

  #container-full-chat {
    margin: 20px;
  }
}
</style>
