<template>

  <div id="event-details-main">
    
    <section id = "title-container">   
        <div id ="text-title">
            <h2>Event title</h2>
        </div>
      
        <div id = "share-button">
            <button>SHARE!</button>
        </div>
        
    </section>

    <section id="details-container">

      <div class="detail">
        <img src="../assets/calendar-img.png" class="users-list-item-picture" />
            <div class="detail-text">
                <h4>DD/MM/YYYY</h4>
                <text>Day, HH:MM - HH:MM</text>
            </div>
        </div>
        
        <div class="detail">
          <img src="../assets/location-img.png" class="users-list-item-picture" />
            <div class="detail-text">
                <h4>Location name</h4>
                <text>Address</text>
            </div>
        </div>

        <div class="detail">
          <img src="../assets/user-img.png" class="users-list-item-picture" />
            <div class="detail-text">
                <h4>Firstname Lastname</h4>
                <text>Organizer</text>
            </div>
            <button id="follow-button">Follow</button>
        </div>

    </section>

    <section id="event-description">
      <h4>About event</h4>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo. sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco</p>
    
    </section>

    <div id="participate-button">
      <button>PARTICIPATE</button>
    </div>

  </div>
    
</template>

<style scoped>

#event-details-main{
  width: 100%;
  height: 100%;
  flex-direction: column;
  display: flex;
}

#title-container {
  background-image: url("../assets/event-details-background.png");
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
    padding-left: 80px;
    font-size: 20px;
    width: 100%
}

#share-button {
    display: flex;
    flex-direction: row;
    justify-content: end;
    width: 100%;
    padding-right: 70px;
}

#share-button button {
    height: 50px;
    width: 120px;
    background-color: black;
    color: white;
    border-radius: 10px;
}

#details-container {
    display: flex;
    height: fit-content;
    flex-flow: row wrap;
    justify-content: space-between;
    margin-left: 70px;
    margin-right: 70px;
    margin-top: 20px;
}

.detail {
    display: flex;
    flex-direction: row;
    align-items: center;
    margin: 10px;
    flex-wrap: wrap;
}

.users-list-item-picture {
  width: 70px;
  height: 70px;
  border-radius: 12px;
}

.detail-text{
    margin-left: 10px;
}

.detail-text h4 {
    font-size: 22px;
    margin-bottom: 3px;
}

.detail-text text {
    font-size: 15px;
    margin-bottom: 3px;
}

#follow-button {
    height: 30px;
    width: 90px;
    font-size: 12px;
    background-color: rgb(225, 219, 219);
    color: black;
    border-radius: 10px;
    margin-left: 50px;
    margin-top: 30px; 
}

#event-description {
  margin-left: 80px;
  margin-right: 80px;
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  height: fit-content;
  line-height: 200%;
}

#event-description p {
  margin-top: 10px;
  text-align: justify;
}

#participate-button {
  margin-top: 100px;
  align-self: center;
}

#participate-button button {
    height: 100px;
    width: 240px;
    background-color: black;
    color: white;
    border-radius: 10px;
    font-size: 22px;
    margin-bottom: 30px;
}

@media (max-width: 530px) {
  .users-list-item-picture {
  width: 40px;
  height: 40px;
}

.detail-text h4 {
    font-size: 16px;
}

.detail-text text {
    font-size: 12px;
}

#details-container {
    margin-left: 40px;
    margin-right: 20px;
    margin-top: 10px;
}

#text-title {
    padding-left: 40px;
    font-size: 16px;
}

#share-button {
    display: flex;
    flex-direction: row;
    justify-content: end;
    width: 70px;
    padding-right: 30px;
}


#event-description {
  margin-left: 50px;
  margin-right: 50px;
  margin-top: 20px;
  line-height: 150%;
}

#event-description p {
  text-align: justify;
  font-size: 14px;
}

#participate-button {
  margin-top: 40px;
  align-self: center;
}

#participate-button button {
    height: 50px;
    width: 120px;
    background-color: black;
    color: white;
    border-radius: 10px;
    font-size: 16px;
    margin-bottom: 30px;
}
    
}

</style>