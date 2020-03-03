<template>
  <div>
    <h1>Contacts</h1>

    <table>
      <th>Name</th>
      <th>Last Name</th>
      <th>Email</th>
      <th>Updated at</th>

      <tr v-for="contact in contacts" :key="contact.first_name">
        <td>{{ contact.first_name }}</td>
        <td>{{ contact.last_name }}</td>
        <td>{{ contact.email }}</td>
        <td>{{ contact.updated_at }}</td>

        <button @click="remove(contact)">Remove</button>
      </tr>
    </table>
    <form @submit.prevent="checkForm" novalidate="true">
      <p>Add new contact</p>

      <p v-if="errors.length">
        <b>Please correct the following error(s):</b>
      </p>
      <ul>
        <li v-for="error in errors" :key="error">{{ error }}</li>
      </ul>
      <br />

      <label for>Name:</label>
      <input type="text" name="name" v-model="newContact.first_name" />
      <label for>Last name:</label>
      <input type="text" name="last_name" v-model="newContact.last_name" />
      <label for>email:</label>
      <input type="email" name="email" v-model="newContact.email" />
      <label for>Date:</label>
      <input type="text" name="date" v-model="newContact.created_at" />

      <button type="submit">Add new contact</button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      contacts: [
        {
          first_name: "Nikola",
          last_name: "Markovic",
          email: "nikola@hotmail.com",
          created_at: "03.02.2020",
          updated_at: "03.02.202"
        }
      ],
      newContact: {},
      errors: []
    };
  },
  methods: {
    checkForm: function() {
      this.errors = [];

      if (!this.newContact.email) {
        this.errors.push("Email required.");
      } else {
        this.addContact();
      }
    },

    addContact() {
      this.newContact.update_at = new Date();
      this.contacts.push(this.newContact);
      this.newContact = {};
    },
    remove(contact) {
      let index = this.contacts.indexOf(contact);
      this.contacts.splice(index, 1);
    }
  }
};
</script>