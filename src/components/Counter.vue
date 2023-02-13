<script setup>
    import { ref } from 'vue';

</script>

<template>
    <div class="counter">
        <h3 class="counter__title">The current count is...</h3>
        <h1 class="counter__digit">{{count}}</h1>
        <div class="counter__input">
            <button class="counter__btn" @click="delCount()">-</button>
            <button class="counter__btn" @click="addCount()">+</button>
        </div>
    </div>

</template>

<style scoped>
    div{
        background-color: rgba(240, 248, 255, 0.671);
        border-radius: .9em 25%;
    }

</style>

<script>
export default{
    methods:{
        delCount(){
            if(this.count >0){
                this.count--;
            }
        },
        addCount(){
            this.count++;
        }
    },
    data(){
        return{
            count: ref(0),
        }
    },
    
    
    
}


</script>

