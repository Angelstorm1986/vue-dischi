<template>
    <div class="d-flex justify-content-center">
        <select name="genre" id="genre" v-model="inputText" @change="changeSearch">
            <option value="">Seleziona il genere che preferisci</option>
            <option :value="genre" v-for="genre in diskGenres" :key="genre">{{genre}}</option>
        </select>
    </div>  
</template>

<script>
export default {
    name:'AppSearch',
    data(){
        return{
            inputText:'',
        }
    },
    props:['diskGenres'],
    methods:{  
        changeSearch(){
            this.$emit('performSearch', this.inputText)
        }
    }
}
</script>

<style lang="scss" scoped>

</style>