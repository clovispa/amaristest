<template>
  <div class="gird-container">
    <div style="    text-align: end; padding: 2px">
      <a @click="save(validateAction.code)" class="myButton-save">{{ validateAction.text }}</a>
    </div>
    <div>
      <a @click="openModal" class="myButton">
        <font-awesome-icon class="search__icon" :icon="['fas', 'minus']"/>
        <span class="span-icon">Eliminar</span>
      </a>
    </div>
        <modal-general   v-if="showModal"
                         @closeModal="closeModal"
                         @deletedUser="deletedUser"
                          :showModal="showModal"/>
  </div>
</template>

<script>
import ModalGeneral from "@/components/componentCrud/common/ModalGeneral";
export default {
  name: "SaveBeneficiary",
  components: {ModalGeneral},
  data() {
    return {
      showModal: false
    }
  },
  props: {
    userItem: {
      type: Object,
      required: false
    }
  },
  computed: {
    validateAction() {
      if(Object.values(this.userItem).length) {
        return { code: 'edit', text: 'Editar'}
      }
      return { code: 'save', text: 'Guardar'}
    }
  },
  methods: {
    save(action) {
      if(action === 'edit') {
        this.$emit('editItem')
      } else {
        this.$emit('save')
      }

    },
    closeModal() {
      this.showModal= false
    },
    openModal() {
      this.showModal= true
    },
    deletedUser() {
      this.$emit('deletedUser')
    }
  }
}
</script>

<style scoped>
.gird-container {
  display: grid;
  grid-template-columns: auto 20%;
}



.myButton {
  background-color:#EE0000;
  border-radius:23px;
  border:1px solid #EE0000;
  display:inline-block;
  cursor:pointer;

  color:#ffffff;
  font-family:Arial;
  font-size:16px;
  padding:5px 18px;
  text-decoration:none;
  text-shadow:0px 0px 2px #EE0000;
}
.myButton:hover {
  background-color:#EE0000;
}
.myButton:active {
  position:relative;
  top:1px;
}
.search__icon {
  width: 33px;
  margin: -3px;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
  border-radius: 100px;
  height: 26px;

  background-color: rgb(258, 0, 0);
}
.span-icon {
  margin-left: 7px;
}
.myButton-save {
  background-color:#283897;
  border-radius:23px;
  border:1px solid #283897;
  display:inline-block;
  cursor:pointer;
  color:#ffffff;
  font-family:Arial;
  font-size:16px;
  padding:5px 18px;
  text-decoration:none;
  text-shadow:0px 0px 2px #283897;
}
</style>
