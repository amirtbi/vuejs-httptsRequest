<template>
    
        <button>
            <slot></slot>
        </button>

</template>

<style scoped>
    /* div.button-container{
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        align-items: center;
    } */
     button{
        padding: 0.5rem 2rem;
        background-color: var(--accentColor);
        border: none;
        outline: none;
        border-radius: 5px;
        font-size: 1rem;
        text-transform: capitalize;
        color: white;
        font-family: inherit;
        cursor:pointer;
        transition: all 0.5s;
        font-weight: bold;
    }
     button:hover{
        
        color:black;
    }
</style>