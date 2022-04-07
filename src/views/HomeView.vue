<script >
export default{
 
}
</script>

<template>
  <div class="h-screen w-screen bg-zinc-900 p-5">
    <h1 class="text-white text-7xl text-center mb-20">Sudoku Solver</h1>
    <div class="flex gap-4">
      <div class="w-[700px] p-5 rounded-xl bg-zinc-800">
        <textarea
          class="h-32 mb-2 resize-none rounded-xl w-full bg-zinc-900 p-3 text-gray-300 font-semibold tracking-widest"
        ></textarea>
        <button
          class="rounded-xl py-3 shadow-2xl shadow-transparent transition-shadow duration-500 hover:shadow-blue-500 text-white w-full bg-blue-500"
        >Solve</button>
      </div>

      <div class="rounded-xl bg-zinc-800 grid grid-cols-9 text-gray-300  p-5">
        <div v-for="x in 81" class=" border w-12 h-12 flex flex-col justify-center font-bold col-span-1 text-center">{{x}}</div>
      </div>
    </div>
  </div>
</template>
