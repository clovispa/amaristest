<template>
  <div
      class="flex-container-card"
      :class="{'isActive' : select === user.id, 'no-isActive' : select !== user.id}"
         @click="selectItem(user)">
    <div>
      <div  class="div-general"
            :class="{'no-div-general' : select === user.id, 'div-general' : select !== user.id}"
      ></div>
    </div>
    <div>
      <div>
        <p class="span-header"><span >Beneficiario</span></p>
      </div>
      <div>
        <p class="letters">{{ user.fullName }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserItem",
 props: {
   user: {
     type: Object,
     required: true
   },
   isActive: {
     type: Boolean,
     default: false
   },
   select: {
     type: [String, Number],
   },
 },
  data() {
    return {
      active: false,
    }
  },
  computed: {
    changeStyle() {
      return  this.user.id === this.user.id
    }
  },
  methods: {
    selectItem (item) {
      this.active = !this.active
      this.$emit('selectUser', item)
    }
  }
}
</script>

<style lang="scss" scoped>
.flex-container-card {
  display: grid;
  grid-template-columns: 22% auto;
  border: 2px solid #eaeaea;
  border-radius: 10px!important;
}
.isActive {
  display: grid;
  grid-template-columns: 22% auto;
  border: 2px solid #283897;
  border-radius: 10px!important;
}
.no-isActive {
  display: grid;
  grid-template-columns: 22% auto;
  border: 2px solid #f5f3f3;
  border-radius: 10px!important;
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
.no-div-general {
  background-color: #283897;
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
  text-align: start;
  margin-left: 19px;
}
.span-header {
  text-align: start;
  margin-bottom: 0px;
  color: #969b98;
  font-size: 14px;
  margin-left: 19px;
}
</style>
