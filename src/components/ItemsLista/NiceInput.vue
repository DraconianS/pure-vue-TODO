<template>
    <div>
        <label>Input:</label>
        <input  type='text'
                placeholder="Input"               
                :value='text' 
                @input="$emit('update:text', $event.target.value)" 
        />
        <button v-show="isEditing" @click="$emit('edited')">DONE</button>
    </div>
</template>

<script>
export default {
    name:'NiceInput',
    props : {
        text: String,
        isEditing: Boolean,
    }
}
</script>
<style scoped>
*{
    @apply leading-4;
}
label{            
    @apply font-sans px-1.5;    
}
input{    
    color: black;    
    @apply bg-gray-200 
            p-1.5 m-1.5 
            border-2 rounded-md border-cyan-700
            focus:outline-none focus:border-red-700;
}
input::placeholder{
    color:inherit;
}
button{
    @apply bg-amber-200
    p-1.5 rounded-sm
    hover:bg-amber-400;
}
</style>