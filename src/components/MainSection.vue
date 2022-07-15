<template>
  <div class="main">
    <div class="container-grid">
      <div>
        <all-beneficiary @sendClean="sendClean"></all-beneficiary>
        <list-beneficiary :users="users" @selectUserItem="selectUserItem"></list-beneficiary>
      </div>
      <div>
        <user-select :userItem="userItem"></user-select>
        <img-beneficiary></img-beneficiary>
      </div>
      <div>
        <form-beneficiary  @editItem="editItem" @userDeleted="userDeleted" @add-user="addUser" :userItem="userItem"></form-beneficiary>
      </div>
    </div>

  </div>
</template>

<script>
import AllBeneficiary from "@/components/componentCrud/AllBeneficiary";
import UserSelect from "@/components/componentCrud/UserSelect";
import ListBeneficiary from "@/components/componentCrud/ListBeneficiary";
import ImgBeneficiary from "@/components/componentCrud/ImgBeneficiary";
import FormBeneficiary from "@/components/componentCrud/FormBeneficiary";
import {mapGetters} from 'vuex'

export default {
  name: "MainSection",
  components: {ListBeneficiary, FormBeneficiary, ImgBeneficiary, UserSelect, AllBeneficiary},
  data() {
    return {
      users: [],
      userItem: {}
    }
  },
  computed: {
    ...mapGetters(['userData',])
  },
  mounted() {
    this.users = this.userData;

  },
  methods: {
    addUser(item) {
      this.users = [...this.users, item]
     },

    selectUserItem (item) {
      this.userItem = item;
    },
    userDeleted(id) {
      this.users = this.users.filter((usr) => usr.id !== id)
    },
    editItem(item) {
      const user = this.users.find( i => i.id === item.id)
      user.fullName = item.fullName;
      user.numCard = item.numCard;
      user.balance = item.balance;

    },
    sendClean() {
      this.userItem = {}
    }
  }
}
</script>

<style lang="scss" scoped>
.container-grid div {
  background: #ffffff;
  padding: 1em;
}
.container-grid {
  display: grid;
  grid-template-columns: 27% 15% auto;
  grid-template-rows: auto auto;
}


</style>
