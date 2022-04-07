<script>
export default{
    props:["puzzle"],
    computed:{
      
    },
    methods:{
        getValue(index){
            if(this.puzzle){
                let puzzleArray = this.puzzle.split("")
                return puzzleArray[index-1] !=="." ? puzzleArray[index-1] :""
            }
        }
    }
}</script>
<template>
    <div class="rounded-xl bg-zinc-800 grid grid-cols-9 text-gray-300 p-5">
        <div
            v-for="x in 81"
            class="border w-12 h-12 flex flex-col justify-center font-bold col-span-1 text-center"
        >{{ getValue(x) }}</div>
    </div>
</template>