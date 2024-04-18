<template>
  <h1>Welcome to My Contact List</h1>
  <div v-for="contact in contacts" :key="contact.id">
    <ContactCard 
      :name="contact.name" 
      :address="contact.address" 
      :phoneNumber="contact.phoneNumber" 
      :email="contact.email"
      @delete="deleteContact(contact)" />
  </div>
  <div>
    <ContactForm 
      :addedContact="newContact" 
      @add="storeContact(newContact)">
    </ContactForm>
  </div>
  <!-- <div>
    <form @submit.prevent>
      <label for="txtName">Name:</label>
      <input type="text" v-model="newContactName" name="txtName" id="txtName"/><br>
      <label for="txtAddress">Address:</label>
      <input type="text" v-model="newContactAddress" name="txtAddress" id="txtAddress"/><br>
      <label for="txtPhoneNumber">Phone Number:</label>
      <input type="text" v-model="newContactPhoneNumber" name="txtPhoneNumber" id="txtPhoneNumber"/><br>
      <label for="txtEmail">Email:</label>
      <input type="text" v-model="newContactEmail" name="txtEmail" id="txtEmail"/><br>

      <button @click="addContact()">Add Contact</button>
    </form>
  </div> -->
  
</template>

<script>
import ContactCard from './ContactCard.vue'
import ContactForm from './ContactForm.vue'

export default {
  data() {
    return {
      // newContactName: '',
      // newContactAddress: '',
      // newContactPhoneNumber: '',
      // newContactEmail: '',
      contacts: [],
      newContact: {
        name: '',
        address: '',
        phoneNumber: '',
        email: ''
      }
    }
  },
  emits: ['contacts'],
  methods: {
    addContact() {
      this.contacts.push(
        { 
          name: this.newContactName, 
          address: this.newContactAddress, 
          phoneNumber: this.newContactPhoneNumber, 
          email: this.newContactEmail 
        }
      )
      this.newContactName = ''
      this.newContactAddress = ''
      this.newContactPhoneNumber = ''
      this.newContactEmail = ''
    },
    storeContact(newContact) {
      this.contacts.push({
        name: newContact.name,
        address: newContact.address,
        phoneNumber: newContact.phoneNumber,
        email: newContact.email
      })
    },
    deleteContact(contact) {
      let index = this.contacts.indexOf(contact)
      this.contacts.splice(index, 1)
    }
  },
  components: {
    ContactCard, ContactForm
  }
}
</script>