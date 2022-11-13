<template>
  <section id="container-timeline">
    <div class="event-timeline">
      <div class="img-date-title-timeline">
        <img src="../assets/default_img.png" alt="logo" />

        <div class="date-title-timeline">
          <h5 class="event-datetime">13/11/2022 - 21:00</h5>
          <h4 class="event-title">GP F1 BRAZIL</h4>
        </div>
      </div>

      <h5 class="event-location">Sao Paulo</h5>
    </div>

    <div class="event-timeline">
      <div class="img-date-title-timeline">
        <img src="../assets/default_img.png" alt="logo" />

        <div class="date-title-timeline">
          <h5 class="event-datetime">23/11/2022 - 17:00</h5>
          <h4 class="event-title">Spain - Costa Rica</h4>
        </div>
      </div>

      <h5 class="event-location">Qatar</h5>
    </div>

    <div class="event-timeline">
      <div class="img-date-title-timeline">
        <img src="../assets/default_img.png" alt="logo" />

        <div class="date-title-timeline">
          <h5 class="event-datetime">18/12/2022 - 16:00</h5>
          <h4 class="event-title">Final Mundial Qatar</h4>
        </div>
      </div>

      <h5 class="event-location">Qatar</h5>
    </div>

    <div class="event-timeline">
      <div class="img-date-title-timeline">
        <img src="../assets/default_img.png" alt="logo" />

        <div class="date-title-timeline">
          <h5 class="event-datetime">1/1/2023 - 23:00</h5>
          <h4 class="event-title">New year party</h4>
        </div>
      </div>

      <h5 class="event-location">Costa Breve</h5>
    </div>

    <div class="event-timeline">
      <div class="img-date-title-timeline">
        <img src="../assets/default_img.png" alt="logo" />

        <div class="date-title-timeline">
          <h5 class="event-datetime">12/2/2023 - 8:00</h5>
          <h4 class="event-title">LSSkying</h4>
        </div>
      </div>

      <h5 class="event-location">La Molina</h5>
    </div>
  </section>
</template>

<style scoped>
img {
  width: 50%;
  height: fit-content;
}

#container-timeline {
  margin: 25px 90px;
  border-left: 5px solid #000;
  padding: 0 20px 0 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.event-timeline {
  background-color: #fafafa;
  padding: 10px 25px;
  box-shadow: 3px 3px 10px 3px rgba(0, 0, 0, 0.2);
  border-radius: 12px;
  flex-basis: 30%;
  display: flex;
  line-height: 1.7;
  position: relative;
  margin-bottom: 10px;
  margin-top: 10px;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
}

.img-date-title-timeline {
  display: flex;
  flex-direction: row;
}

.date-title-timeline {
  padding-bottom: 7px;
  padding-top: 7px;
  padding-left: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: stretch;
}

.event-timeline::before {
  content: "";
  border-radius: 50%;
  background-color: #000;
  border: 2px solid #000;
  display: block;
  width: 10px;
  height: 10px;
  position: absolute;
  top: 35px;
  left: -40px;
}

/*MEDIA QUERIES*/
@media (max-width: 768px) {
  #container-timeline {
    margin: 25px;
    flex-wrap: wrap;
  }

  .event-timeline {
    flex-wrap: wrap;
    padding: 5px 12px;
  }

  h4 {
    font-size: 0.9em;
    font-weight: bold;
  }

  h5 {
    font-size: 0.7em;
  }
}
</style>
