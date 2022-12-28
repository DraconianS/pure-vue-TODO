<template>
    <div class="wrapper">
        <NiceInput v-model:text="desc" :isEditing='isEditing' @edited="edited" />
        <AddButton :items="this.items" @addItem="addItem" />
        <div class='item-wrapper' v-for="(i,index) in this.items" :key="index">
            <div class='items'>{{'Item #'+ (index + 1)}}
                <p>{{i.desc}}</p>
            </div>
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
            items:[],
            counter:0,
            desc:'',
            eIndex: null,
            isEditing: false,
        };
    },
    watch:{
        items:{
            handler(newItems, oldItems){                
                localStorage.setItem('items', JSON.stringify(newItems) );
            },
            deep:true
        }
    },
    beforeMount(){        
        this.items = JSON.parse(localStorage.getItem('items')) ?? [];
    },
    methods: {
        addItem(){
            this.counter++;
            this.items.push({
                id: this.counter,
                desc: this.desc,                
            });
            this.desc = '';
            // localStorage.setItem('items', this.items);
        },
        delItem(itemId){
            this.isEditing = false;
            this.items = this.items.filter(e => e.id != itemId);                        
            // localStorage.setItem('items', this.items);
        },
        startEdit(index){
            this.eIndex = index;
            this.isEditing = true;
            this.desc = this.items[index].desc;
        },
        edited(){
            this.items[this.eIndex].desc = this.desc;
            this.desc = '';
            this.isEditing = false;
            // localStorage.setItem('items', this.items);
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
*{
    @apply leading-5
}
.item-wrapper{
    @apply bg-rose-200 w-96 rounded-md
    mx-1.5;
}
.items{
    @apply mx-1.5 my-0.5
}
p{
    @apply bg-yellow-50 rounded-sm px-1 indent-2 text-justify break-words
}
.wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 5px;
}
</style>