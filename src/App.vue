<template>
  <learning-survey></learning-survey>
  <user-experiences
    
  ></user-experiences>
</template>

<script>
import LearningSurvey from "./components/Survey/LearningSurvey.vue";
import UserExperiences from "./components/Survey/UserExperiences.vue";
export default {
  components: {
    LearningSurvey,
    UserExperiences,
  },
  data() {
    return {
    

      savedSurveyResults: [],
    };
  },
  //disabling methods due to use of fetchApi and firebase
  // methods:{
  //   storeSurvey(surveyData){
     
  //     const result = {
  //       name:surveyData.name,
  //       rating:surveyData.rating,
  //       id:new Date().toISOString
  //     };
  //     this.savedSurveyResults.push(result);
  //   }
  // }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Karla:wght@300&display=swap");
:root {
  --primaryColor: #02044a;
  --secondaryColor: #dddddd;
  --textColor: white;
  --accentColor: #25cc88;
}
html,
body {
  margin: 0;
  padding: 0;
  font-family: "Karla", sans-serif;
}
* {
  box-sizing: border-box;
}
</style>
