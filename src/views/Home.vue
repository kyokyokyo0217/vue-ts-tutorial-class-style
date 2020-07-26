<template>
  <div class="home">
    <p>{{ greetText }}</p>
    <p>Total Greeting: {{ count }}</p>
    <p v-if="isVip">You're VIP User!!</p>
    <p>
      <my-button :greet="greetText" :count="count" @clicked="onMyButtonClicked">Greet</my-button>
    </p>
    <p>
      <reset-button @clicked="onResetButtonClicked"></reset-button>
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Watch, Vue } from "vue-property-decorator";
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

@Component({
  components: {
    MyButton,
    ResetButton
  }
})
export default class Home extends Vue {
  private count: number = 0;
  public greetText: string = "Hello!!";

  //computed property
  public get isVip(): boolean {
    return this.count >= 5;
  }

  /** ライフサイクルフック */
  public created() {
    console.log("created");
  }

  @Watch("count")
  public gotVip() {
    if (this.count === 5) {
      alert("Congratulations! Now You're VIP!");
    }
  }

  public onMyButtonClicked(count: number) {
    this.greetText = "Hello Again!!";

    this.count++;
  }

  public onResetButtonClicked() {
    this.count = 0;
    this.greetText = "Hello!!";
  }
}
</script>
