<template>
    <div>
        <h1>TODO it!</h1>
        <div class="inputBox shadow">
        <input type="text" v-model="searchKeyword" placeholder="Search Keyword" 
        v-on:keyup.enter="search">
        <span><button>검색</button></span>
    </div>
    <select v-model="selected">
        <option v-for="option in options"  v-bind:key="option.key">{{ option.text }}</option>
    </select>
    </div>
</template>

<script>
export default {
    data(){
        return{
            searchKeyword:'',
            selected: 'A',
            options: [
                { text: 'One', key: 'A' },
                { text: 'Two', key: 'B' },
                { text: 'Three', key: 'C' }
            ]
            }
        }
    }
    methods : {
        // search() {
        //     //console.log("search method실행"+this.searchKeyword);
        //     if(this.searchKeyword !==""){
        //         var word=this.searchKeyword && this.searchKeyword.trim();
        //         this.$emit('search',word);
        //     }else{
        //         alert('검색어를 입력해 주세요');
        //     }
        // }
    }

</script>

<style scoped>
    h1{
        color : #2f3b52;
        font-weight : 900;
        margin : 2.5rem 0 1.2rem;
    }
</style>