<template>
    <div class="addItem">
        <input type="text" class="input" id="name-input" v-model="item.name"/>
        <font-awesome-icon
            icon="plus-circle"
            :class="[item.name?'active':'inactive' , 'plus']"
            @click="addItem()"
        />
    </div>
</template>
<script>
export default {
    data:function(){
        return{
            item:{
                name : ""
            }
        }
    },
    methods:{
        addItem(){
            if(this.item.name == ''){
                return;
            }else{
                axios.post('api/item/store',{
                    item : this.item
                })
                .then(response=>{
                    if(response.status == 201){
                        this.item.name == "";
                        this.$emit('reloadlist')
                        document.getElementById('name-input').value = '';
                    }
                })
                .catch(error=>{
                    console.log(error);
                });
            }
        }
    }
}
</script>
<style scoped>
.addItem{
    display: flex;
    justify-content: center;
    align-items: center;
}
input{
    background: #f7f7f7;
    border: 2px solid #215f43;
    outline: none;
    padding: 5px;
    margin: 10px;
    border-radius: 7px;
    width: 270px;
}
.plus{
    font-size: 30px;
}
.active{
    color: #121212;
}
.inactive{
    color: #f9f9f9;
}
</style>
