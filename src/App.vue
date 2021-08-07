<template>
  <div id="app">
    <Grid
      :grid="maze.grid"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Grid from "./components/Grid.vue";
/* eslint-disable */
import Client, { GeneratorAlgorithm, Maze, Point, SolverAlgorithms } from 'maze';

@Component({
  components: {
    Grid,
  },
})
export default class App extends Vue {

  private client = new Client();

  private get maze(): Maze {
    const generated = this.client.generate(10, 10, GeneratorAlgorithm.RECURSIVE_DIVISION);

    const solution = this.client.solve(generated, new Point(0, 0), new Point(9, 9), SolverAlgorithms.A_STAR);

    console.log(solution);

    return solution?.solution ?? generated;
  }

  computed() {
    console.log('Computed');

    return {

    };
  }

}
</script>