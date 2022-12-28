<template>
    <button @click="$emit('editItem')">Edit </button>
</template>
<script>
export default {
    name:'EditButton',
}
</script>
<style scoped>
button{
    @apply px-1.5 mx-1.5
    bg-amber-200
    rounded-sm
    hover:bg-amber-400;
}
</style>