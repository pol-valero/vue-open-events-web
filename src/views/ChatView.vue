<template>
  <div id="chat-main">
    <section id="container-chat-person">
      <h4 id="chats-title">Friends</h4>
      <ul>
        <li>
          <button class="btn-chat">
            <div class="chat-person">
              <img class="little-img" src="../assets/default_img.png" alt="logo" />
              <h5 class="name-padding">Ángel García</h5>
            </div>
          </button>
        </li>

        <li>
          <button class="btn-chat">
            <div class="chat-person">
              <img class="little-img" src="../assets/default_img.png" alt="logo" />
              <h5 class="name-padding">Claudia Lajara</h5>
            </div>
          </button>
        </li>

        <li>
          <button class="btn-chat">
            <div class="chat-person">
              <img class="little-img" src="../assets/default_img.png" alt="logo" />
              <h5 class="name-padding">Pol Valero</h5>
            </div>
          </button>
        </li>

        <li>
          <button class="btn-chat">
            <div class="chat-person">
              <img class="little-img" src="../assets/default_img.png" alt="logo" />
              <h5 class="name-padding">Marc Geremias</h5>
            </div>
          </button>
        </li>
      </ul>
    </section>
    <section id="container-chat-interactive">
      <div id="container-chat-person-selected">
        <img class="little-img" src="../assets/default_img.png" alt="logo" />
        <RouterLink to="/profile" id="friend-profile-btn">
          <h5 id="name-big-padding">Marc Geremias</h5>
        </RouterLink>
      </div>

      <div id="container-full-chat">
        <div class="my-message">
          <h4 class="message">Com vas amb web?</h4>
          <h6>9:03</h6>
        </div>

        <div class="other-message">
          <div>
            <h4 class="message">Em falta 1 vista</h4>
            <h6>9:32</h6>
          </div>
        </div>

        <div class="my-message">
          <h4 class="message">Jo estic acabant aquesta</h4>
          <h6>9:54</h6>
        </div>

        <div class="my-message">
          <h4 class="message">Recorda que s'entrega en poc</h4>
          <h6>9:54</h6>
        </div>

        <div class="other-message">
          <div>
            <h4 class="message">Si si, demà ho acabo</h4>
            <h6>9:32</h6>
          </div>
        </div>
      </div>

      <div id="container-chat-input">
        <input type="text" placeholder="Message" />
        <button class="btn-chat"><i class="material-icons">send</i></button>
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

/*MEDIA QUERIES*/
@media(min-width: 768px) {
  #chat-main {
    flex-direction: row;
  }

  #container-full-chat {
    margin: 20px;
  }
}
</style>
