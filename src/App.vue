<template>
  <learning-survey></learning-survey>
  <user-experiences :user-experiences="enteredUserExperiences"></user-experiences>
</template>


<script>
import LearningSurvey from './components/Survey/LearningSurvey.vue';
import UserExperiences from './components/Survey/UserExperiences.vue';
export default {
  components:{
    LearningSurvey,
    UserExperiences
  },
  data(){
    return{
      enteredUserExperiences:[
        {
          id:"AMIR",
          name:"AMIR",
          rating:"Poor"
        },
        {
          id:"ALI",
          name:"ALI",
          rating:"Average"
        }
      ]
    }
}
}
</script>


<style >
@import url('https://fonts.googleapis.com/css2?family=Karla:wght@300&display=swap');
:root{
  --primaryColor:#02044a;
  --secondaryColor:#dddddd;
  --textColor:white;
  --accentColor:#25CC88;
  
}
html,body{
  margin: 0;
  padding: 0;
  font-family: 'Karla', sans-serif;
}
*{
  box-sizing: border-box;
}

</style>