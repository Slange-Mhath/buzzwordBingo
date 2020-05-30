<template>
  <div>
    <form>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
        <textarea class="form-control" rows="3" v-model="buzzword.buzzword"></textarea>
      </div>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
        <button class="btn btn-primary" @click.prevent="createNew">Add Buzzword</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      buzzword: {
        buzzword: ""
      }
    };
  },
  methods: {
    createNew() {
      this.$emit("buzzwordAdded", this.buzzword.buzzword);
      this.buzzword.buzzword = "";
    }
  }
};
</script>

<style></style>