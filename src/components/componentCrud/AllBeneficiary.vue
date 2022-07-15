<template>
<div class="gird-container">
  <div class="container-beneficiary">
    <p class="span-header"><span >Todos los</span></p>
    <p class="letters"> Beneficiarios</p>
  </div>
  <div>
    <a @click="clean" class="myButton">
      <font-awesome-icon class="search__icon" :icon="['fas', 'plus']"/>
      <span class="span-icon">Nuevo</span>
    </a>
  </div>

</div>
</template>

<script>
export default {
  name: "AllBeneficiary",
  methods: {
    clean() {
      this.$emit('sendClean')
    }
  }
}
</script>

<style lang="scss" scoped>
.container-beneficiary {
  margin-top: 0px;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
}
.gird-container {
  display: grid;
  grid-template-columns: 50% 50%;
}
.letters {
  Size: 14px;
  Line-height:19.36px;
  font-weight: bold;
  margin-top: 0px;
  text-align: start;
}
.span-header {
  text-align: start;
  margin-bottom: 0px;
  color: #969b98;
  font-size: 14px;
}


.myButton {
  background-color:#283897;
  border-radius:23px;
  border:1px solid #283897;
  display:inline-block;
  cursor:pointer;
  color:#ffffff;
  font-family:Arial;
  font-size:16px;
  padding-left: 6px!important;
  padding:5px 18px;
  text-decoration:none;
  text-shadow:0px 0px 2px #283897;
}
.search__icon {
  width: 33px;
  margin: -3px;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
  border-radius: 100px;
  height: 26px;
  background-color: rgba(72,86,167)
}
.span-icon {
  margin-left: 7px;
}


</style>
