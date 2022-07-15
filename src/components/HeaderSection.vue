<template>
<div class="header">
  <div class="flex-container">
    <div>
      <div  class="div-general"></div>
    </div>
    <div class="container-header">
      <p class="span-header"><span >Sodexo Suite</span></p>
      <p class="letters">Administración de Beneficiario</p>
    </div>

  </div>
</div>
</template>

<script>
export default {
  name: "HeaderSection"
}
</script>

<style lang="scss" scoped>
.container-header {
  margin-top: 0px;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
}
.flex-container {
  display: flex;
  justify-content: flex-start;
  flex-direction: row;
  height: 85%;
}

.div-general {
  background-color: #F3F3F3;
  width: 50px;
  margin: 14px;
  text-align: center;
  min-height: 50px;
  font-size: 20px;
  border-radius: 100px ;
}
.letters {
  Size: 14px;
  Line-height:19.36px;
  font-weight: bold;
  margin-top: 0px;
}
.span-header {
  text-align: start;
  margin-bottom: 0px;
  color: #969b98;
  font-size: 14px;
}
</style>
