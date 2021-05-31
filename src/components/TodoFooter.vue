<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">Clear All</span>
        <button @click="checkProps">check</button>
    </div>
</template>

<script>
export default {
    methods:{
        clearTodo(){
            this.$emit('removeAll');
        },
        checkProps(){
            console.log('여기는 footer~');
            this.$emit('check');
        }
    }
}
</script>

<style scoped>
   .clearAllContainer{
        width:8.5rem;
        height: 50px;
        line-height: 50px;
        background-color:white;
        border-radius: 5px;
        margin:0 auto;
    }
    .clearAllBtn{
        color:#e20303;
        display:black;
    }
</style>