<template>
  <div class="grid-wrapper">
    <div
      v-for="(columnValue, columnIndex) in grid"
      :key="columnIndex"
      class="grid-column"
    >
      <div
        v-for="(node, rowIndex) in columnValue"
        :key="rowIndex"
      >
        <NodeWrapper
          :node="node"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Grid } from 'maze';
import NodeWrapper from './NodeWrapper.vue';

@Component({
  components: {
    NodeWrapper
  }
})
export default class GridComponent extends Vue {
  @Prop()
  private grid!: Grid;

  mounted() {
    console.log(this.grid);
  }
}
</script>

<style scoped>
.grid-wrapper {
  display: flex;
  flex-direction: row;
  flex-grow: 0;
}

.maze-entry {
  background-color: white;
  width: 50px;
  height: 50px;
  /* border-right: 1px solid black;
  border-bottom: 1px solid black; */
}
</style>
