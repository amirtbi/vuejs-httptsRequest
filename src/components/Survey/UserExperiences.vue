<template>
  <base-card>
    <div class="experiences-container">
      <div class="experiences-container__title">
        <h2>Submitted experiences</h2>
        <base-button @click="loadExperiences">Load Data</base-button>
      </div>
      <div v-if="isLoading" class="lds-dual-ring"><div></div></div>
      <p class="caution-meessage" v-else-if="!isLoading && error ">
          {{error}}
      </p>
      <p
        class="caution-meessage"
        v-else-if="!isLoading && (!results || results.length === 0)"
      >
        No stored experience found! Sart storing experience...
      </p>
      <ul v-else-if="!isLoading && results && results.length > 0">
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
const axios = require("axios");
export default {
  data() {
    return {
      results: [],
      isLoading: false,
      error:null
    };
  },
  methods: {
    loadExperiences() {
      //load data using fetchApi
      this.isLoading = true;
      //using axios
      axios.get('https://vue-http-demo-cc5c5-default-rtdb.firebaseio.com/survey.json')
        .then(response=>{
          //console.log(response.data);
            return response.data;
            
        })
      // fetch("https://vue-http-demo-cc5c5-default-rtdb.firebaseio.com/survey.json")
      //   .then((response) => {
      //     if (response.ok) {
      //       return response.json();
      //     }
      //   })
        .then((data) => {
          
          this.isLoading = false;
          const result = [];
          for (const item in data) {
            result.push({
              id: item,
              name: data[item].name,
              rating: data[item].chosenRating,
            })
          }
          this.results = result;
        })
        .catch(error=>{
                console.log(error);
                this.isLoading = false;
                this.error = "Something is wrong!. Please try again!";
            });

       
    },
  },
  mounted() {
    this.loadExperiences();
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
/*loading style */
.lds-dual-ring {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: center;
  width: 100%;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 20px;
  height: 20px;
  margin: 8px;
  border-radius: 50%;
  border: 6px solid var(--accentColor);
  border-color: var(--accentColor) transparent var(--accentColor) transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.caution-meessage {
  color: #a59f9e !important;
  padding: 0.5rem 1rem !important;
  font-size: 1.2rem !important;
  width: 100%;
  text-align: center;
}
</style>
