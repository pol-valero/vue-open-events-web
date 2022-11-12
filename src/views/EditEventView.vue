<template>
  <div id="create-event-main">
    <section id = "title-container">
      <h2>Edit event</h2>
    </section>

    <section id="forms-container">
      <div class="single-form">
        <h4 class="form-title">Title</h4>  
        <input class="field" type="text"  placeholder="House BBQ"/>
      </div>

      <div class="single-form">
        <h4 class="form-title">Description</h4>  
        <textarea class="textarea" name="Text1" cols="40" rows="5" placeholder="This event is fun!"></textarea>
      </div>
      
      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Start date</h4>  
          <input class="field"  type="date" value = "2022-11-04" />
        </div>
        <div class="single-form">
          <h4 class="form-title" >End date</h4>  
          <input class="field"  type="date" value = "2022-11-06"/>
        </div>
      </div>

      <div class="single-form">
        <h4 class="form-title">Location</h4>  
        <input class="field"  type="text"  placeholder="Teruel"/>
      </div>

      <div class="single-form">
        <h4 class="form-title">Image</h4>  
        <input class="field" type="url" placeholder="www.url-of-current-img.com"  />
      </div>

      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Type</h4>  
          <input class="field"  type="text" placeholder="Sports" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Capacity</h4>  
          <input class="field"  type="number" value="50"  />
        </div>
      </div>

      <div class="button-container">
        <button onclick="location.href='/eventDetails';" class="save-button">SAVE CHANGES</button>
        <button onclick="location.href='/eventDetails';" class="cancel-button">CANCEL</button>
      </div>
    </section>
  </div>
</template>

<style scoped>
/*aside {
  display: none;
}*/

#create-event-main {
  width: 100%;
  height: 100%;
  flex-direction: column;
  display: flex;
}

#title-container {
  margin-top: 30px;
  margin-bottom: 20px;
  text-align: center;
  font-size: 15px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

#forms-container {
  display: flex;
  flex-direction: column;
  width: 40%;
  align-self: center;
  padding: 30px;    
  background-color: #eeeeff;
  border-radius: 10px;
  margin-bottom: 50px;
}

.single-form {
  display: flex;
  flex-direction: column;
  margin: 5px;
}

.dual-form {
  display: flex;
  flex-flow: row wrap;
}

.dual-form div {
  flex-grow: 1;
}

.textarea {
  resize: none;
  background-size: 20px;
  background-position: 8px;
  background-color: white;
  border-radius: 10px;
  margin-bottom: 7px;
  margin-top: 5px;
  padding-block: 7px;
  padding-inline: 7px;
  border: #ccc solid 2px;
}

.textarea:focus {
  border: #7722ff solid 2px;
  outline: none;
}

.button-container {
  margin: 30px;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-evenly;
}

.save-button {
  background-color: black;
  color: white;
  border-radius: 10px;
  border: none;
  height: 50px;
  width: 170px;
  margin: 10px;
  transition: 0.1s;
}

.save-button:hover {
  background-color: #7722ff;
  opacity: 1;
  box-shadow: 4px 5px 5px rgba(0, 0, 0, 0.5);
}

.cancel-button {
  background-color: white;
  color: #7722ff;
  border-radius: 10px;
  border: #7722ff solid 2px;
  height: 50px;
  width: 170px;
  margin: 10px;
}

.cancel-button:hover {
  box-shadow: inset 0px 0px 5px 2px rgba(0, 0, 0, 0.3);
}

.field {
  background-size: 20px;
  background-position: 8px;
  background-color: white;
  border-radius: 10px;
  margin-bottom: 7px;
  margin-top: 5px;
  padding-block: 7px;
  padding-inline: 7px;
  border: #ccc solid 2px;
}

.field:focus {
  border: #7722ff solid 2px;
  outline: none;
}

@media (max-width: 650px) {
  #forms-container{
    width: 60%;
    padding: 20px;
  }

  .button-container {
    margin: 10px;
  }
}
</style>