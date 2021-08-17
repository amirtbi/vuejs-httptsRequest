<template>
    <div class="card-container">
        <slot></slot>
    </div>
</template>


<style scoped>
div.card-container{
    display: flex;
    flex-direction: column;
    background-color: var(--primaryColor);
    box-shadow: 0px 2px 12px 4px #ccc;
    width: 600px;
    
    margin: 3rem auto;

}
</style>