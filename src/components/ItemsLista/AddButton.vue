<template>
    <button @click="$emit('addItem')">Add + </button>
</template>
<script>
export default {
    name: 'AddButton',
}
</script>