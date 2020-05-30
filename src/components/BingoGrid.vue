<template>
  <div class="row">
    <cmp-buzzword
      v-for="(buzzword, index) in buzzwordlist"
      :key="buzzword.index"
      @click.native="deleteBuzzword(index)"
    >{{ buzzword.buzzword }}</cmp-buzzword>
    <!-- .native treats click on cmp like clicks on template -->
  </div>
</template>

<script>
import Buzzword from "./Buzzword.vue";
export default {
  props: ["buzzwordlist"],
  components: {
    cmpBuzzword: Buzzword
  },
  methods: {
    deleteBuzzword(index) {
      this.$emit("buzzwordDeleted", index);
    }
  }
};
</script>

<style></style>