<style scoped>

/*aside {
  display: none;
}*/

#create-event-main{
  width: 100%;
  height: 100%;
  flex-direction: column;
  display: flex;
}

#title-container {
  margin: 20px;
  text-align: center;
  font-size: 15px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

#forms-container {
  display: flex;
  flex-direction: column;
  width: 30%;
  align-self: center;
}

.single-form{
  display: flex;
  flex-direction: column;
  margin: 5px;
}

.dual-form{
  display: flex;
  flex-flow: row wrap;
}

.dual-form div {
  flex-grow: 1;
}

.textarea {
  resize: none
}

.button-container {
  margin: 30px;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-evenly;
}

.create-event-button {
  margin: 5px;
  background-color: black;
  color: aliceblue;
  padding: 10px;
}

.cancel-button{
  margin: 5px;
  padding: 10px;
}

</style>


<template>

  <div id="create-event-main">
    
    <section id = "title-container">
      <h2>Edit event</h2>
    </section>

    <section id="forms-container">
      <div class="single-form">
        <h4 class="form-title">Title</h4>  
        <input type="text"  value="House BBQ"/>
      </div>

      <div class="single-form">
        <h4 class="form-title">Description</h4>  
        <textarea class="textarea" name="Text1" cols="40" rows="5" >This event is fun!</textarea>
      </div>
      
      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Start date</h4>  
          <input type="date" value = "2022-11-04" />
        </div>
        <div class="single-form">
          <h4 class="form-title" >End date</h4>  
          <input type="date" value = "2022-11-06"/>
        </div>
      </div>

      <div class="single-form">
        <h4 class="form-title">Location</h4>  
        <input type="text"  value="Teruel"/>
      </div>

      <div class="single-form">
        <h4 class="form-title">Image</h4>  
        <input type="url" value="www.url-of-current-img.com"  />
      </div>

      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Type</h4>  
          <input type="text" value="Sports" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Capacity</h4>  
          <input type="number" value="50"  />
        </div>
      </div>

      <div class="button-container">
        <button class="create-event-button">SAVE CHANGES</button>
        <button class="cancel-button">CANCEL</button>
      </div>
      
    </section>

  </div>
    
</template>