<template>
  <form @submit.prevent>
    <label for="txtName">Name:</label>
    <input type="text" v-model="newContact.name" name="txtName" id="txtName"/>
    <label for="txtAddress">Address:</label>
    <input type="text" v-model="newContact.address" name="txtAddress" id="txtAddress"/>
    <label for="txtPhoneNumber">Phone Number:</label>
    <input type="text" v-model="newContact.phoneNumber" name="txtPhoneNumber" id="txtPhoneNumber"/>
    <label for="txtEmail">Email:</label>
    <input type="text" v-model="newContact.email" name="txtEmail" id="txtEmail"/>

    <button @click="$emit('add', newContact)">Add Contact</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newContact: {
        name: this.newName,
        address: this.newAddress,
        phoneNumber: this.newPhoneNumber,
        email: this.newEmail
      }
    }
  },
  props: ['newName', 'newAddress', 'newPhoneNumber', 'newEmail']
}
</script>