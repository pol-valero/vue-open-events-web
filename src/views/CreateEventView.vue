<script>

import FormInput from "../components/formInputText.vue";
import FormInputTextArea from "../components/formInputTextArea.vue";

 export default {
    name: "CreateEventView",
    components: { FormInput, FormInputTextArea },
    data() {
        return {
          eventTitle: '',
          eventDescription: '',
          eventStartDate: '',
          eventEndDate: '',
          eventLocation: '',
          eventImage:'',
          eventType:'',
          eventCapacity: 0
        };
    },
    mounted() {
        // We show the aside and the header
        this.$root.$data.show.aside = false;
    },
    methods: {
      prova () {
        if (this.eventDescription === "prova") {
          alert("Bien")
        } else {
          alert('Mal')
        }
      },
      goToHome () {
        this.$router.push("/")
      },
      goToEventDetails () {
        this.$router.push("/eventDetails")
      }
    },
};
</script>

<template>
  <div id="create-event-main">
    <section id="title-container">
      <h2>Create event</h2>
    </section>

    <section id="forms-container">
      <div class="single-form">
        <FormInput
          v-on:update-modelValue="(x) => this.eventTitle = x"
          title =  "Title"
          defaultTxt = "Ex.- House BBQ"
        />
      </div>

      <div class="single-form">
        <FormInputTextArea
          v-on:update-modelValue="(x) => this.eventDescription = x"
          title =  "Description"
          defaultTxt = "Ex.- This event is fun!"
        />
      </div>

      <div class="dual-form">
        <div class="single-form">
          <h4 class="form-title">Start date</h4>
          <input class="field" type="date" />
        </div>
        <div class="single-form">
          <h4 class="form-title">End date</h4>
          <input class="field" type="date" />
        </div>
      </div>

      <div class="single-form">
        <FormInput
          v-on:update-modelValue="(x) => this.eventLocation = x"
          title =  "Location"
          defaultTxt = "Ex.- Teruel"
        />
      </div>

      <div class="single-form">
        <FormInput
          v-on:update-modelValue="(x) => this.eventImage = x"
          title =  "Image"
          defaultTxt = "Ex.- www.url-of-current-img.com"
        />
      </div>

      <div class="dual-form">
        <div class="single-form">
          <FormInput
          v-on:update-modelValue="(x) => this.eventType = x"
          title =  "Type"
          defaultTxt = "Ex.- Sports"
          />
        </div>
        <div class="single-form">
          <h4 class="form-title">Capacity</h4>
          <input class="field" type="number" placeholder="Ex.- 50" />
        </div>
      </div>

      <div class="button-container">
        <button
          v-on:click="goToEventDetails()"
          class="create-event-button primary-button"
        >
          CREATE EVENT
        </button>
        <button
          v-on:click="goToHome(), prova()"
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
  align-self: center;
  width: 70%;
  padding: 15px;
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

.create-event-button {
  height: 50px;
  width: 170px;
  margin: 10px;
}

.cancel-button {
  height: 50px;
  width: 170px;
  margin: 10px;
}

@media (min-width: 768px) {
  #forms-container {
    width: 40%;
    padding: 30px;
  }

  .button-container {
    margin: 30px;
  }
}
</style>
