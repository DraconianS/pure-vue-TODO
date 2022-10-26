<template>
    <button @click="editItem(this.item)">Edit </button>
</template>
<script>
export default {
    name:'EditButton',
    props:{
        item:Object,
        
    },
    methods:{
        editItem: (item) =>{
            alert('editItem here id:' + item.id);
        }
    },
}
</script>