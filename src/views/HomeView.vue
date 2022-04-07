<script >
import PuzzleInput from "../components/PuzzleInput.vue";
import SudokuMatrice from "../components/SudokuMatrice.vue";
import SudokuSolver from "../scripts/SudokuSolver"

export default {
  components: { PuzzleInput, SudokuMatrice },
  data() {
    return {
      puzzle: "1.5..2.84..63.12.7.2..5.....9..1....8.2.3674.3.7.2..9.47...8..1..16....926914.37.",
      error: "",
      solving: false
    }
  },
  methods: {
    setValue(value) {
      this.puzzle = value;

    },
    async solve() {
      this.solving = true
      this.error = ""
      const solver = new SudokuSolver()
      let puzzle = this.puzzle
      if (puzzle == undefined) {
        res.json({ error: 'Required field missing' })
        this.solving = false;

        return;
      }
      if (solver.validate(puzzle) !== true) {
        this.error = solver.validate(puzzle).error
        this.solving = false;
        return;
      }
      let result = await solver.solve(puzzle, (x) => {

        this.puzzle = x
      });
      if (result == false) {
        this.error = "Puzzle cannot be solved";
        this.solving = false;
        return;
      }
      // this.puzzle = result
      this.solving = false;
    }

  }
}
</script>

<template>
  <div class="min-h-screen min-w-screen bg-zinc-900 p-5">
    <h1 class="text-white text-6xl text-center mt-14">Sudoku Solver</h1>
    <h1 class="text-white text-center my-8" >This Sodoku solver uses backtracking algorithm a brute force algorithm more info  <a class="text-blue-400 hover:text-blue-500 " target="#blank" href="https://en.wikipedia.org/wiki/Sudoku_solving_algorithms#Backtracking">here</a></h1>
    <div class="flex gap-10 justify-center">
      <div class="flex flex-col">
        <PuzzleInput
          @inputChanged="setValue($event)"
          @solveClicked="solve()"
          :puzzle="puzzle"
          :solving="solving"
          class="self-baseline mb-4"
        />

        <div v-if="error" class="text-red-500">
          <span>Error :</span>
          <span>{{ error }}</span>
        </div>
      </div>

      <SudokuMatrice :puzzle="puzzle" />
    </div>
  </div>
</template>
