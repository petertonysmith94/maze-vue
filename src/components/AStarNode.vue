<template>
  <div
    class="node-entry"
    v-bind:class="{
      north: this.north,
      east: this.east,
      south: this.south,
      west: this.west
    }"
  >
    ({{ node.coordinate.x }}, {{ node.coordinate.y }})
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import {
  Node as NodeModel,
  Entity as EntityModel,
  AStarNode as AStarNodeModel
} from 'maze';

@Component
export default class AStarNode extends Vue {
  @Prop()
  private node!: AStarNodeModel;

  get data() {
    return {
      color: 'black'
    };
  }

  get north()  {
    return this.node && this.node.north === EntityModel.WALL;
  }

  get east()  {
    return this.node && this.node.east === EntityModel.WALL;
  }

  get south()  {
    return this.node && this.node.south === EntityModel.WALL;
  }

  get west()  {
    return this.node && this.node.west === EntityModel.WALL;
  }
}
</script>

<style scoped>
.node-entry {
  background-color: var(--color);
  width: 50px;
  height: 50px;
  border: 1px solid white;
}

.node-entry.north {
  border-top: 1px solid black;
}

.node-entry.east {
  border-right: 1px solid black;
}

.node-entry.south {
  border-bottom: 1px solid black;
}

.node-entry.west {
  border-left: 1px solid black;
}
</style>
