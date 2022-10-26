<template>
    <div>
        <AddButton :items="this.items" @addItem="addItem" />
        <div v-for="(i,index) in this.items" :key="index">
            <p>{{'#'+ (index + 1) + ' Desc: ' + i.desc}}</p>
            <edit-button :item=i />
            <delete-button :item=i @delItem="delItem(i.id)" />
        </div>
            
    </div>    
</template>

<script>
import AddButton from "./ItemsLista/AddButton.vue";
import DeleteButton from './ItemsLista/DeleteButton.vue';
import EditButton from './ItemsLista/EditButton.vue';

export default{
    data(){
        return{
            items: [],
            counter:0,
        };
    },
    methods: {
        addItem(){
            this.counter++;
            this.items.push({
                id: this.counter,
                desc:'this is a desc',
            });            
        },
        delItem(itemId){            
            console.log(this.items.filter(e => e.id == itemId)[0].id);
            this.items = this.items.filter(e => e.id != itemId);            
        }
    },  
    components : {
        AddButton,
        EditButton,
        DeleteButton,        
    },
};
</script>

<style scoped>

</style>