<template>
  <form @submit.prevent>
    <label for="txtName">Name:</label>
    <input type="text" v-model="newContact.name" name="txtName" id="txtName"/><br>
    <label for="txtAddress">Address:</label>
    <input type="text" v-model="newContact.address" name="txtAddress" id="txtAddress"/><br>
    <label for="txtPhoneNumber">Phone Number:</label>
    <input type="text" v-model="newContact.phoneNumber" name="txtPhoneNumber" id="txtPhoneNumber"/><br>
    <label for="txtEmail">Email:</label>
    <input type="text" v-model="newContact.email" name="txtEmail" id="txtEmail"/><br>

    <button @click="addNewContact(newContact)">Add Contact</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newContact: this.addedContact
    }
  },
  methods: {
    addNewContact(newContact) {
      this.$emit('add', newContact)
      this.newContact.name = ''
      this.newContact.address = ''
      this.newContact.phoneNumber = ''
      this.newContact.email = ''
    }
  },
  props: {
    addedContact: {
      type: Object
    }
  }
}
</script>