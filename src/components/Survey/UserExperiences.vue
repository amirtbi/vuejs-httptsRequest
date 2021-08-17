<template>
<base-card>
    <div class="experiences-container">
        <ul>
        <li v-for="experience in userExperiences" :key="experience.id">
            <p>
            <strong>{{ experience.name }}</strong> rated the learning
            <strong>{{experience.rating}}</strong>
            </p>
        </li>
        </ul>

    </div>
  </base-card>
</template>

<script>


export default {
  props: ["userExperiences"],

  data() {
    return {};
  },
};
</script>

<style scoped>
    ul{
        list-style: none;
        margin: 0;
        padding: 0;
        
    }
    li{
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        align-items: center;
        padding: 0.5rem 1.2rem;
    }
    p{
        color: var(--textColor);
        font-size: 1rem;
        font-family: inherit;
        font-weight:normal;

        padding: 0;
        margin: 0;
    }
    p strong{
        color: var(--accentColor);
    }
</style>
