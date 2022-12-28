<template>
    <button @click="$emit('addItem')">Add + </button>
</template>
<script>
export default {
    name: 'AddButton',
}
</script>
<style scoped>
button{
    margin: 2px 1rem;
    padding: 5px;
    text-align: center;    
    @apply bg-green-600 leading-4 rounded-sm w-60;
}
button:hover{
    @apply brightness-125;
}
</style>