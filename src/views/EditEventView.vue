<script>

export default {
  name: "EditEventView",
  data() {
    return { //TODO: posar al gust
      title: "",
      description: "",
      startDate: "",
      endDate: "",
      location: "",
      image: "",
      type: "",
    };
  },

  mounted() {
    // We hide the aside
    this.$root.$data.show.aside = false;
  },

  methods: {
  },
};
</script>

<template>
  <div id="create-event-main">
    <section id="title-container">
      <h2>Edit event</h2>
    </section>

    <section id="forms-container">
      <div class="single-form">
        <h4 class="form-title">Title</h4>
        <input class="field" type="text" placeholder="House BBQ" />
      </div>

      <div class="single-form">
        <h4 class="form-title">Description</h4>
        <textarea
          class="textarea field"
          name="Text1"
          cols="40"
          rows="5"
          placeholder="This event is fun!"
        ></textarea>
      </div>

      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Start date</h4>
          <input class="field" type="date" value="2022-11-04" />
        </div>
        <div class="single-form">
          <h4 class="form-title">End date</h4>
          <input class="field" type="date" value="2022-11-06" />
        </div>
      </div>

      <div class="single-form">
        <h4 class="form-title">Location</h4>
        <input class="field" type="text" placeholder="Teruel" />
      </div>

      <div class="single-form">
        <h4 class="form-title">Image</h4>
        <input
          class="field"
          type="url"
          placeholder="www.url-of-current-img.com"
        />
      </div>

      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Type</h4>
          <input class="field" type="text" placeholder="Sports" />
        </div>
        <div class="single-form">
          <h4 class="form-title">Capacity</h4>
          <input class="field" type="number" value="50" />
        </div>
      </div>

      <div class="button-container">
        <button
          onclick="location.href='/eventDetails';"
          class="save-button primary-button"
        >
          SAVE CHANGES
        </button>
        <button
          onclick="location.href='/eventDetails';"
          class="cancel-button secondary-button"
        >
          CANCEL
        </button>
      </div>
    </section>
  </div>
</template>

<style scoped>
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
  width: 60%;
  align-self: center;
  padding: 20px;
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
}

.button-container {
  margin: 10px;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-evenly;
}

.save-button {
  height: 50px;
  width: 170px;
  margin: 10px;
}

.cancel-button {
  height: 50px;
  width: 170px;
  margin: 10px;
}

#forms-container {
  width: 60%;
  padding: 20px;
}

@media (min-width: 650px) {
  #forms-container {
    width: 40%;
    padding: 30px;
  }

  .button-container {
    margin: 30px;
  }
}
</style>
