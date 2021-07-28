<template>
    <div>
        <div v-for="(item ,index) in items" :key="index">
            <!-- v-on is for child item and should make a another eventlister on app -->
            <list-item
                :item="item"
                class="item"
                v-on:itemchanged="$emit('reloadlist')"
            />
        </div>
    </div>
</template>
<script>
import listItem from "./listItem.vue"
export default {
    props:['items'] ,
    components:{
        listItem
    }
}
</script>
<style scoped>
.item{
    background: #e6e6e6;
    padding: 10px;
    margin-top: 5px;
    border-radius: 10px;

}
</style>
