<template>
  <div class="container">
    <cmpNewBuzzword @buzzwordAdded="newBuzzword"></cmpNewBuzzword>
    <cmpBingoGrid :buzzwordlist="buzzwordlist" @buzzwordDeleted="deleteBuzzword"></cmpBingoGrid>
  </div>
</template>

<script>
import BingoGrid from "./components/BingoGrid.vue";
import NewBuzzword from "./components/NewBuzzword.vue";

export default {
  data: function() {
    return {
      maxBuzzwords: 20,
      indexForBuzzword: 0,
      buzzwordlist: [
        {
          index: this.indexForBuzzword,
          buzzword: "",
          checked: Boolean
        }
      ]
    };
  },
  methods: {
    newBuzzword(buzzword) {
      if (this.buzzwordlist.length >= this.maxBuzzwords) {
        return alert("To many buzzwords. Please delete one first");
      }
      this.buzzwordlist.push({
        index: this.indexForBuzzword,
        buzzword: buzzword,
        checked: false
      });
      this.indexForBuzzword++;
    },
    deleteBuzzword(index) {
      this.buzzwordlist.splice(index, 1);
    }
  },
  components: {
    cmpBingoGrid: BingoGrid,
    cmpNewBuzzword: NewBuzzword
  }
};
</script>

<style>
cldmenu li:before,
.cldmenu li:after {
  -webkit-transition: all 0.35s ease;
  transition: all 0.35s ease;
  height: 2px;
  width: 35%;
  background-color: #004f71;
  position: absolute;
  content: "";
  opacity: 0;
}

.cldmenu li:before {
  top: 0;
  left: 0;
}

after,
:before {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
</style>
