<style>

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
  flex-direction: row;
}

.dual-form div {
  flex-grow: 1;
}


</style>

<template>
  <div id="create-event-main">
    
    <section id = "title-container">
      <h2>Create event</h2>
    </section>

    <section id="forms-container">
      <div class="single-form">
        <h4 class="form-title">Title</h4>  
        <input type="text" />
      </div>

      <div class="single-form">
        <h4 class="form-title">Title</h4>  
        <input type="text" />
      </div>
      
      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Title</h4>  
          <input type="text" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Title</h4>  
          <input type="text" />
        </div>
      </div>

      <div class="single-form">
        <h4 class="form-title">Title</h4>  
        <input type="text" />
      </div>

      <div class="single-form">
        <h4 class="form-title">Title</h4>  
        <input type="text" />
      </div>

      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Title</h4>  
          <input type="text" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Title</h4>  
          <input type="text" />
        </div>
      </div>
      
      
    </section>

  </div>
    
      
  

</template>
