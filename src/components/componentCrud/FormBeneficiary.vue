<template>
  <div >
    <save-beneficiary @save="save" @deletedUser="deletedUser" @editItem="editItem" :userItem="userItem"/>
    <form  class="form-container">
      <label  class="text-form" >Nombre completo</label>
      <input v-model="userForm.fullName" maxlength="60" type="text" placeholder="Nombre completo" >
      <label class="text-form">No. de tarjeta</label>
      <input v-model="userForm.numCard" maxlength="50" type="number" placeholder="Numero de tarjeta">
      <label class="text-form">Saldo</label>
      <input v-model="userForm.balance" maxlength="50" type="number" placeholder="Estado de cuenta"  >
    </form>
    <div v-if="error.length">
          <ul>
        <li v-for="e in error" :key="e.id" class="error-class"> {{e}}</li>
           </ul>
    </div>
  </div>
</template>

<script>


import SaveBeneficiary from "@/components/componentCrud/SaveBeneficiary";

export default {
  name: "FormBeneficiary",
  components: {SaveBeneficiary},
  props: {
    userItem: {
      type: Object,
      required: false
    }
  },
  data() {
    return {
      userForm: {
        fullName: '',
        numCard: '',
        balance: '' ,
        id: ''
      },
      error:[],
      validation: false

    }
  },

  watch: {
    'userItem' () {
      this.userForm = Object.assign({} , this.userItem)
      this.userForm.balance = this.currency(this.userForm.balance)
      this.error=[];
    }
  },


  methods: {
    currency (value) {
      return  '' + parseFloat(value).toFixed(2)
    },
    validate() {
      this.validation = false;
      this.error=[];
      if(!this.userForm.fullName) {
        this.error.push("Nombre no  puede ir vacío")
          return
      }
      let expReg= /^(?=.{1,20}$)(('|-|\s|\.|\(|\)?)([A-zÑñ]('|-|\s|\.|\(|\))?)\1?)+$/
      if(!expReg.test(this.userForm.fullName)) {
        this.error.push("Nombre no  puede llevar caracteres especiales")
        return;
      }
      if(!this.userForm.numCard) {
        this.error.push("Número de tarjeta no puede ser vacío")
        return;
      }
      if(!this.userForm.balance || isNaN(this.userForm.balance )) {
        this.error.push("Saldo  no puede ser vacío")
        return;
      }
      this.validation = true;
    },

    save() {
      this.validate()

      if(this.validation) {
        this.error=[];
        const newUser = {
          id: Date.now(),
          fullName: this.userForm.fullName,
          numCard: this.userForm.numCard,
          balance: this.userForm.balance,
        }
        this.$emit('add-user', newUser)
        this.userForm.fullName= '';
        this.userForm.numCard= '';
        this.userForm.balance= '';
        this.userForm.id = '';
      }

    },
    deletedUser () {
      this.userForm.fullName= '';
      this.userForm.numCard= '';
      this.userForm.balance= '';
      this.userForm.id = '';
      this.$emit('userDeleted', this.userItem.id)
    },
    editItem() {
      this.validate()
      if(this.validation) {
      this.$emit('editItem',  this.userForm)
      }
    }
  }
}
</script>

<style lang="scss" scoped>

.error-class {
  color: red;
}
.container-grid {
  display: grid;
  grid-template-columns: 100%;

}
.form-container {
  max-width: 300px;
  padding: 10px;
  background-color: white;
}


.form-container input[type=text] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  border: none;
  background: #f1f1f1;
  width: 100vh;
  font-weight: bold;
}
.text-form {
  text-align: start;
  margin-bottom: 0px;
  color: #969b98;
  font-size: 12px;
}
.form-container input[type=number] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  border: none;
  background: #f1f1f1;
  width: 100vh;
  font-weight: bold;
}

</style>
