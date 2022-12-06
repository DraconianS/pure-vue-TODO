<template>
    <div class="bg-pink-500">
        <NiceInput v-model:text="desc" :isEditing='isEditing' @edited="edited" />
        <AddButton :items="this.items" @addItem="addItem" />
        <div v-for="(i,index) in this.items" :key="index">
            <p>{{'#'+ (index + 1) + ' Desc: ' + i.desc}}</p>
            <edit-button @editItem='startEdit(index)' />
            <delete-button :item=i @delItem="delItem(i.id)" />
        </div>
            
    </div>    
</template>

<script>
import AddButton from "./ItemsLista/AddButton.vue";
import DeleteButton from './ItemsLista/DeleteButton.vue';
import EditButton from './ItemsLista/EditButton.vue';
import NiceInput from './ItemsLista/NiceInput.vue';

export default{
    data(){
        return{
            items: [],
            counter:0,
            desc:'',
            eIndex: null,
            isEditing: false,
        };
    },
    methods: {
        addItem(){
            this.counter++;
            this.items.push({
                id: this.counter,
                desc: this.desc,                
            });
            this.desc = '';
        },
        delItem(itemId){                        
            this.items = this.items.filter(e => e.id != itemId);            
        },
        startEdit(index){
            this.eIndex = index;
            this.isEditing = true;
            this.desc = this.items[index].desc;
        },
        edited(){
            this.items[this.eIndex].desc = this.desc;
            this.edited = null;
            this.desc = '';
            this.isEditing = false;
        }
    },  
    components : {
        AddButton,
        EditButton,
        DeleteButton,
        NiceInput,        
    },
};
</script>

<style scoped>

</style>