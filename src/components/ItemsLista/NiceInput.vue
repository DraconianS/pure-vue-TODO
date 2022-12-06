<template>
    <div>
        <label>Input: </label>
        <input  type='text'
                placeholder="input"               
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