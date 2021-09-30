<template>

    <div class="col-12 d-flex justify-content-center">

        <label class="text-white pe-3" for="ms_select">Choose a filter:</label>

        <select id="ms_select"  @change="getSelectValue(), $emit('Change', selectValue)" >

            <option value="All">All</option>
            <option v-for='(element, index) in optionArray' :key='index' :value="element"> {{ element }}</option>
            
        </select> 

    </div>

</template>

<script>
export default {
    name: 'Select',
    props: ['albumList'],
    data : function(){
        return{
            optionArray : [],
            selectValue : 'All',
        }
    },

    methods : {
        getSelectValue(){
            this.selectValue = document.getElementById('ms_select').value;
            
        }
    },

    created : function(){
        this.albumList.filter((element) => {
            let genre = element.genre;
            if (!this.optionArray.includes(genre)){
                this.optionArray.push(genre)
            }
            
        });
    }

}
</script>

<style lang='scss' scoped>
@import '../style/variables.scss';

label{
    font-size: 1.25rem;
    font-weight: 600;
}


</style>

function filteredItems(array, filter){

    if (filter.trim().toLowerCase() === 'all'){
        return array
    }

    return array.filter((element) => element.type == filter);
        
}