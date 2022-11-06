<style>

/*aside {
  display: none;
}*/

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
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
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
    height: 100px;
    flex-direction: row;
    justify-content: space-between;
    margin-left: 70px;
    margin-right: 70px;
}

.detail {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.users-list-item-picture {
  width: auto;
  height: 60%;
  border-radius: 12px;
}

.detail-text{
    margin-left: 10px;
}

.detail-text h4 {
    font-size: 22px;
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
}

</style>


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
            <img src="../assets/default_img.png" class="users-list-item-picture" />
            <div class="detail-text">
                <h4>DD/MM/YYYY</h4>
                <h7>Day, HH:MM - HH:MM</h7>
            </div>
        </div>
        
        <div class="detail">
            <img src="../assets/default_img.png" class="users-list-item-picture" />
            <div class="detail-text">
                <h4>Location name</h4>
                <h7>Address</h7>
            </div>
        </div>

        <div class="detail">
            <img src="../assets/default_img.png" class="users-list-item-picture" />
            <div class="detail-text">
                <h4>Firstname Lastname</h4>
                <h7>Organizer</h7>
            </div>
            <button id="follow-button">Follow</button>
        </div>

    </section>

  </div>
    
</template>