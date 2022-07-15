<template>
  <div class="gird-container">
    <div>
      <p class="span-header"><span >Usuario seleccionado</span></p>
    </div>
    <div>
      <p class="letters">{{ userItem.fullName}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserSelect",
  props: {
    userItem: {
      type: Object,
      required: false
    }
  },
}
</script>

<style lang="scss" scoped>
.gird-container {
  display: grid;
  grid-template-columns: 100%;
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

</style>
