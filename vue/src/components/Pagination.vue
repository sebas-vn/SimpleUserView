<template>
  <div id="pages">
    <span class="disabled"> <strong> < </strong> </span>
    <span>1</span>
    <span> <strong> > </strong> </span>
  </div>
</template>

<script>
export default {
  name: "Pagination"
};
</script>

<style scoped>
  #pages {
    margin: 50px 0px 0px 0px;
    display: flex;
    justify-content: center;
    width: 100%;
  }

  span {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px;
    background-color: #48BC85;
    cursor: pointer;
    border-radius: 50%;
    width: 15px;
    height: 15px;
    transition: 0.5s;
    margin: 0px 10px 0px 10px
  }

  span:hover{
    box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.5);
  }

  .disabled {
    background-color: rgba(72,188,133, 0.1);
    cursor: default;
    color: rgba(0,0,0,0.1);
    box-shadow: 0px 0px 0px rgba(0, 0, 0, 0) !important;
  }
</style>