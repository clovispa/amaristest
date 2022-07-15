<template>
<div class="sidebar  ">
  <div class="responsive-img">
    <img src="../assets/Logo2.png" alt="Nature" class="responsive">
  </div>
  <div class="flex-container">
    <div class="div-general"></div>
    <div class="div-general"></div>
    <div class="div-general" ></div>
  </div>
  <div>
    <div  class="div-general"></div>
  </div>
</div>
</template>

<script>
export default {
  name: "SidebarSection"
}
</script>

<style lang="scss" scoped>
.flex-container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  background-color: #363A3E;
  height: 80%;
}
.flex-container div {
  background-color: #505457;
  width: 50px;
  margin: 10px;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
  border-radius: 100px ;
}
.responsive {
  text-align: center;
  padding: 13px;
}
.responsive-img {
  text-align: center;
  background-color: white;
  height: 8%;
}
.div-general {
  background-color: #505457;
  max-width: 50px;
  margin: 10px;
  text-align: center;
  min-height: 50px;
  font-size: 20px;
  border-radius: 100px ;
}
.div-back {
  background-color: #2c3e50;
}
</style>
