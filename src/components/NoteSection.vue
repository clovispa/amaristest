<template>
  <div class="note">
    <div class="flex-container">
      <div class="div-general"></div>
      <div class="div-general-sub" ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NoteSection"
}
</script>

<style lang="scss" scoped>
.flex-container {
  display: flex;
  justify-content: flex-end;
  flex-direction: row;
  background-color: #ffffff;
  height: 85%;
}
.flex-container div {
  width: 200px;
  margin: 10px;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
  border-radius: 100px ;
}
.div-general {
  background-color: #F3F3F3;
  max-width: 50px!important;
  margin: 14px;
  text-align: center;
  min-height: 50px;
  font-size: 20px;
  border-radius: 100px ;
}
.div-general-sub{
  background-color: #F3F3F3;
}
</style>
