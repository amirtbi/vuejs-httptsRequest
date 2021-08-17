<template>
  <base-card>
    <div class="experiences-container">
      <div class="experiences-container__title">
        <h2>Submitted experiences</h2>
        <base-button @click="loadExperiences">Load Data</base-button>
      </div>
      <ul>
        <li v-for="experience in results" :key="experience.id">
          <p>
            <strong>{{ experience.name }}</strong> rated the learning
            <strong>{{ experience.rating }}</strong>
          </p>
        </li>
      </ul>
    </div>
  </base-card>
</template>

<script>
export default {
  data() {
    return {
      results: [],
    };
  },
  methods: {
    loadExperiences() {
      fetch(
        "https://vue-http-demo-cc5c5-default-rtdb.firebaseio.com/survey.json"
      )
        .then((response)=> {
          if (response.ok) {
            return response.json();
          }
        })
        .then((data)=> {
         
          const result = [];
          for (const id in data) {
            result.push({
              id: id,
              name: data[id].name,
              rating: data[id].chosenRating,
            });
           
          }
          this.results = result;
        });
    },
  },
};
</script>

<style scoped>
div.experiences-container__title {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
}
h2 {
  color: white;
  margin: 0;
  padding: 1rem 1.2rem;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
li {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  padding: 2rem;
  margin: 1rem;
  border: 1px solid var(--accentColor);
  border-radius: 5px;
}
p {
  color: var(--textColor);
  font-size: 1rem;
  font-family: inherit;
  font-weight: normal;

  padding: 0;
  margin: 0;
}
p strong {
  color: var(--accentColor);
}
</style>
