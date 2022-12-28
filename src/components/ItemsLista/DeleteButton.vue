<template>
    <button @click="$emit('delItem')">Delete - </button>
</template>
<script>
export default {
    name:'DeleteButton',
}
</script>
<style scoped>
button{
    @apply px-1.5 mx-1.5
    bg-red-400
    rounded-sm
    hover:bg-red-600;
}
</style>