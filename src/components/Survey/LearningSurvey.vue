<template>
  <base-card>
    <form class="form-control" @submit.prevent="storeSurveyData">
      <div class="form-title">
        <h1>How Was Your Learning Experience?</h1>
      </div>
      <div class="form-row">
        <label for="username">Your Name</label>
        <input type="text" name="username" id="username" v-model.trim="name" />
      </div>
      <div class="form-column">
        <h2 id="form-column__title">My Learning Experience was ...</h2>
        <div class="form-column__row">
          <input
            type="radio"
            name="user-rating"
            value="Poor"
            id="poor-rating"
            v-model="rating"
          />
          <label for="poor-rating">Poor</label>
        </div>
        <div class="form-column__row">
          <input
            type="radio"
            name="user-rating"
            value="Average"
            id="average-rating"
            v-model="rating"
          />
          <label for="average-rating">Average</label>
        </div>
        <div class="form-column__row">
          <input
            type="radio"
            name="user-rating"
            value="Great"
            id="great-rating"
            v-model="rating"
          />
          <label for="great-rating">Great</label>
        </div>
      </div>
      <div class="form-row" v-if="formValidity === 'invalid'">
        <small id="caution-message">There is at least one empty field!</small>
      </div>
      <div v-else-if="error" class="form-row">
        <small id="caution-message">{{ error }}</small>
      </div>
      <div class="button-container">
        <base-button>SUBMIT</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
const axios = require('axios');
async function postServey(postData) {
  try{
    await axios.post(
     "https://vue-http-demo-cc5c5-default-rtdb.firebaseio.com/survey.json",
     postData
   )

  }
  catch(error){
    console.log(error,"something went wrong!?");
  }
}

export default {
  //   emits: ["submitSurvey"],
  data() {
    return {
      name: "",
      rating: null,
      formValidity: "pending",
      error: null,
    };
  },
  methods: {
    storeSurveyData() {
      //   const userEnteredExperience = {
      //     id: new Date().toISOString,
      //     name: this.name,
      //     rating: this.rating,
      //   };

      if (this.name === "" || TouchList.rating === "") {
        this.formValidity = "invalid";
        return;
      }

      this.formValidity = "valid";
      //when not using fetchAPI
      //   this.$emit("submitSurvey", userEnteredExperience);
     
      this.error = null;
      const postData = { name: this.name, chosenRating: this.rating };
      postServey(postData)
      .catch(error=>{
        throw new Error(error);
      })
       //using fetchAPI
      // fetch(
      //   "https://vue-http-demo-cc5c5-default-rtdb.firebaseio.com/survey.json",
      //   {
      //     method: "POST",
      //     headers: {
      //       "Content-Type": "application/json",
      //     },
      //     body: JSON.stringify({ name: this.name, chosenRating: this.rating }),
      //   }
      // )
      //   .then((response) => {
      //     if (response.ok) {
      //       ///
      //     } else {
      //       //throw new Error("....");
      //       throw "Could not save the data !";
      //     }
      //   })
      //   .catch((error) => {
      //     console.log(error);
      //     this.error = error;
      //     //when using new Error(...)
      //     //this.error = error.message
      //   });
      this.rating = null;
      this.name = "";
    },
  },
};
</script>

<style scoped>
div.form-title {
  display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: flex-start;
  align-items: center;
}
div.form-title h1 {
  font-family: inherit;
  font-weight: bold;
  font-size: 1.4rem;
  margin: 0;
  padding: 1.2rem;
  color: var(--textColor);
}
form.form-control {
  display: flex;
  flex-direction: column;
  width: 100%;
  justify-content: center;
  align-items: flex-start;
}
div.form-row {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
  padding: 1.2rem;
}
div.form-column {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  padding: 0.2rem 1.2rem;
}
h2#form-column__title {
  color: var(--textColor);
  font-family: inherit;
  font-weight: bold;
  font-size: 1.1rem;
}
div.form-column__row {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
div.form-column__row input,
div.form-column__row label {
  margin: 0.2rem;
}

div.form-row input {
  width: 60%;
  border: 2px solid var(--accentColor);
  outline: none;
  padding: 0.4rem 1rem;
  border-radius: 5px;
  background-color: var(--primaryColor);
  color: var(--secondaryColor);
  font-size: 0.9rem;
}
div.form-row label {
  margin-right: 0.4rem;
}
label {
  color: var(--secondaryColor);

  font-family: inherit;
  font-weight: bold;
}
div.button-container {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  padding: 1.2rem;
}
small#caution-message {
  color: orange;
  font-family: inherit;
  font-size: 1.1rem;
  font-weight: bold;
}
</style>
