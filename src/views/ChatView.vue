<style scoped>

/* People */
.little-img {
  width: 40px;
  height: 40px;
}

hr {
  width: 100%;
}

#chat-main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
}

#container-chat-person {
  background-color: rgb(252, 244, 244);
  padding: 15px;
  display: flex;
  flex-direction: column;
}

.chat-person {
  margin-top: 10px;
  margin-bottom: 3px;
  display: flex;
  flex-direction: row;
  align-items: center;
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
  color: #25d366;
  transition: 0.4s;
  cursor: pointer;
}
/* Messages */
#container-chat-interactive {
  background-color: #dcf8c6;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
}

#container-chat-person-selected {
  background-color: #ece5dd;
  padding: 10px 15px;
  display: flex;
  flex-direction: row;
  align-items: center;
}

#name-big-padding {
  padding-left: 10px;
  font-size: 16px;
  font-weight: bold;
}

#container-full-chat {
  margin: 20px;
  display: flex;
  flex-direction: column;
}

.my-message h4 {
  border: #25d366 12px solid;
  border-radius: 30px;
  background-color: #25d366;
  margin-bottom: 5px;
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
  border: #ece5dd 12px solid;
  border-radius: 30px;
  background-color: #ece5dd;
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
  background: #dcf8c6;
  padding: 10px;
  margin-bottom: 5px;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

input {
  width: 80%;
  padding: 5px;
  margin-right: 5px;
}

.message {
  font-size: 13px;
}
/*MEDIA QUERIES*/
@media (max-width: 768px) {
  #container-full-chat {
    margin: 10px;
  }
}
</style>

<template>
  <div id="chat-main">
    <section id="container-chat-person">
      <h4 id="chats-title">Chats</h4>

      <button class="btn-chat">
        <div class="chat-person">
          <img
            class="little-img"
            src="../assets/default_img.png"
            alt="logo"
          />
          <h5 class="name-padding">Ángel García</h5>
        </div>
        <hr />
      </button>

      <button class="btn-chat">
        <div class="chat-person">
          <img
            class="little-img"
            src="../assets/default_img.png"
            alt="logo"
          />
          <h5 class="name-padding">Claudia Lajara</h5>
        </div>
        <hr />
      </button>

      <button class="btn-chat">
        <div class="chat-person">
          <img
            class="little-img"
            src="../assets/default_img.png"
            alt="logo"
          />
          <h5 class="name-padding">Pol Valero</h5>
        </div>
        <hr />
      </button>

      <button class="btn-chat">
        <div class="chat-person">
          <img
            class="little-img"
            src="../assets/default_img.png"
            alt="logo"
          />
          <h5 class="name-padding">Marc Geremias</h5>
        </div>
        <hr />
      </button>
    </section>

    <section id="container-chat-interactive">
      <div id="container-chat-person-selected">
        <img
          class="little-img"
          src="../assets/default_img.png"
          alt="logo"
        />
        <h5 id="name-big-padding">Marc Geremias</h5>
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

        <div class="other-message">
          <div>
            <h4 class="message">Per cert, recorda fer el peer2peer!</h4>
            <h6>9:32</h6>
          </div>
        </div>
      </div>

      <div id="container-chat-input">
        <input type="text" />
        <button class="btn-chat"><i class="material-icons">send</i></button>
      </div>
    </section>
  </div>
</template>
