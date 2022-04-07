<script>
export default {
    props: ["puzzle", "solving"],
    data() {
        return {}
    },
    methods: {
        emitValue() {

            this.$emit("inputChanged", this.$refs.textArea.value);
        }
    }
}

</script>
<template>
    <div class="w-[700px] p-5 rounded-xl bg-zinc-800">
        <ol class="list-disc ml-4 text-gray-300 mb-4">
            <li>Ensure that there is 81 charchter</li>
            <li>
                <span class="text-3xl">.</span>& numbers are the only allowed charachters
            </li>

          
        </ol>
        <textarea
            :readonly="solving"
            @input="emitValue"
            ref="textArea"
            :value="puzzle"
            class="h-32 mb-2 resize-none rounded-xl w-full bg-zinc-900 p-3 text-gray-300 font-semibold tracking-widest"
        ></textarea>
        <button
            v-if="!solving"
            @click="$emit('solveClicked')"
            class="rounded-xl py-3 shadow-2xl shadow-transparent transition-shadow duration-500 hover:shadow-blue-500 text-white w-full bg-blue-500"
        >Solve</button>

        <div class="flex justify-center py-2" v-if="solving">
            <svg
                class="animate-spin h-5 w-5 text-blue-500"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
            >
                <circle
                    class="opacity-25"
                    cx="12"
                    cy="12"
                    r="10"
                    stroke="currentColor"
                    stroke-width="4"
                />
                <path
                    class="opacity-75"
                    fill="currentColor"
                    d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
                />
            </svg>
        </div>
    </div>
</template>