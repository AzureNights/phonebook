<script setup>
import AddContactForm from './components/AddContactForm.vue';
import AddressBookTable from './components/AddressBookTable.vue';
import { ref, onMounted } from 'vue';

const addBook = ref([]) // the array where each contact will be added to 

onMounted(() => {
  const savedContacts = localStorage.getItem('addBook');
  if (savedContacts) { 
    addBook.value = JSON.parse(savedContacts);
  }
});

function addItemToAddressBook(newContact) {
  addBook.value.push(newContact);
  localStorage.setItem('addBook', JSON.stringify(addBook.value));
};

// export default {
//   components: {
//     AddContactForm,
//     AddressBookTable
//   },
// };

// };

</script>


<template>
  <main class="flex flex-row p-10 gap-8 w-350 bg-black left-400">
      <div id="form" class="w-1/3 p-2 bg-blue-500">

      <AddContactForm @add-contact="addContactToBook" />
    </div>

    <div id="table" class="w-2/3 p-6 gap-8 bg-cyan-500">
      <AddressBookTable :contacts="contacts" />
    </div>
  </main>
</template>

