<template>
  <base-card>
    <form class="form-control" @submit.prevent>
      <div class="form-title">
        <h1>How Was Your Learning Experience?</h1>
      </div>
      <div class="form-row">
        <label for="username">Your Name</label>
        <input type="text" name="username" id="username" />
      </div>
      <div class="form-column">
        <h2 id="form-column__title">My Learning Experience was ...</h2>
        <div class="form-column__row">
          <input type="radio" name="user-rating" id="poor-rating" />
          <label for="poor-rating" value="poor">Poor</label>
        </div>
        <div class="form-column__row">
          <input type="radio" name="user-rating" id="average-rating" />
          <label for="average-rating" value="average">Average</label>
        </div>
        <div class="form-column__row">
          <input type="radio" name="user-rating" id="great-rating" />
          <label for="great-rating" value="great">Great</label>
        </div>
      </div>
      <div class="button-container">
          <base-button>SUBMIT</base-button>
      </div>
    </form>
  </base-card>
</template>

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
div.button-container{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    padding: 1.2rem;
}
</style>
