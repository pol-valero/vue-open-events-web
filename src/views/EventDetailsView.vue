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
  height: 30%;
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

#button-title {
    display: flex;
    flex-direction: row;
    justify-content: end;
    width: 100%;
    padding-right: 100px;
}

#button-title button {
    height: 50px;
    width: 120px;
}


</style>


<template>

  <div id="event-details-main">
    
    <section id = "title-container">
       
        <div id ="text-title">
            <h2>Create event</h2>
        </div>
      
        <div id = "button-title">
            <button>Share</button>
        </div>
        
    </section>

    <section id="details-container">
      
      
    </section>

  </div>
    
</template>