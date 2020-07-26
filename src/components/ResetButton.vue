<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from "vue-property-decorator";

@Component
export default class ResetButton extends Vue {
  private initialValue!: string;

  /** モデルバインドのために記述必須 */
  @Emit()
  public clicked() {}

  public onClick() {
    this.clicked();
  }
}
</script>
