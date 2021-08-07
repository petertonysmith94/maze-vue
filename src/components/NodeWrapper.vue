<template>
  <component
    v-bind:is="component"
    :node="node"
  />
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import {
  Entity as EntityModel,
  Node as NodeModel,
  AStarNode
} from 'maze';
import NodeComponent from './Node.vue';
import AStarNodeComponent from './AStarNode.vue';

@Component({
  components: {
    NodeComponent,
    AStarNodeComponent
  }
})
export default class NodeWrapper extends Vue {
  @Prop()
  private node!: NodeModel;

  private get component() {
    if (this.node instanceof AStarNode) {
      return AStarNodeComponent;
    }

    return NodeComponent;
  }

  mounted() {


    // if (this.node instanceof NodeModel) {
    //   console.log('Node');
    // }

    // if (this.node instanceof AStarNode) {
    //   console.log('AStarNode');
    // }
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
.maze-entry {
  background-color: white;
  width: 50px;
  height: 50px;
  border: 1px solid white;
}

.maze-entry.north {
  border-top: 1px solid black;
}

.maze-entry.east {
  border-right: 1px solid black;
}

.maze-entry.south {
  border-bottom: 1px solid black;
}

.maze-entry.west {
  border-left: 1px solid black;
}
</style>
