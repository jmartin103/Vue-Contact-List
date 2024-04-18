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
</template>

<script>
import ContactCard from './ContactCard.vue'
import ContactForm from './ContactForm.vue'

export default {
  data() {
    return {
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