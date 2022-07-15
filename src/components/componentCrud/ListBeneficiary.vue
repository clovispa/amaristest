<template>
  <div class="list-beneficiary">
    <div class="search__container">
      <input v-model="keyword" type="text" class="search-input" placeholder="Buscar">
      <font-awesome-icon class="search__icon" :icon="['fas', 'search']"/>
    </div>
    <h1></h1>
    <div class="gird-container">
      <div class="flex-container">
        <div>
              <user-item
                  class="item-content"
                  v-for="user in filteredList"
                  :key="user.id"
                  @click="selectUserItem(user)"
                  :select="select"
                  :user="user" @selectUser="selectUser"/>
        </div>
      </div>
    </div>

  </div>

</template>

<script>
import UserItem from "@/components/userComponent/UserItem";
export default {
  name: "ListBeneficiary",
  components: {UserItem},
  props: {
    users: {
      type: Array,
      required: true
    }
  },
  data() {
  return{
    keyword: '',
    isActive: false,
    select: ''
  }
},
  computed: {
    filteredList() {
      return this.users.filter((str) => {
        return str.fullName.toLowerCase().includes(this.keyword.toLowerCase());
      });
    }
  },
  methods: {
    selectUserItem(item) {
      this.select = item.id;
    },
    selectUser(item) {
      this.select = item.id;
      this.$emit('selectUserItem', item)
    }
  }
}
</script>

<style  lang="scss" scoped>
.list-beneficiary{
  background: #E5E5E5!important;
  min-height: 50vh;
}
.flex-container {
  flex-direction: row;
}
.gird-container {
  display: grid;
  grid-template-columns: 100%;
}
.flex-container-card {
  display: grid;
  grid-template-columns: 20% auto;
}


.div-general {
  background-color: #F3F3F3;
  width: 50px;
  margin: 14px;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
  border-radius: 100px ;
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
.item-content {
  background: #ffffff;
  margin: 5px;
  border-radius: 10px!important;


}
.search__icon {
  position: absolute;
  color: #BFBFBF;
  left: 15px;
}

.search__container {
  position: relative;
  align-items: center;
  display: flex;
  justify-content: center;
  color: black;

  .search-input {
    width: 100%;
    background: #EAEBEB;
    border: 1px;
    padding: 0 43px;
    height: 40px;
    border-radius: 10px;
    font-size: 0.9rem;

  }
}


</style>
