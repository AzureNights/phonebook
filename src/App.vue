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

function addContactToBook(newContact) {
  addBook.value.push(newContact);
  localStorage.setItem('addBook', JSON.stringify(addBook.value));
};

function removeContact(index) {
  addBook.value.splice(index, 1);
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
  <main class="flex flex-row p-10 gap-8 w-350 left-400">
      <div id="form" class="w-1/3 p-2">

      <AddContactForm @add-contact="addContactToBook" />
    </div>

    <div id="table" class="w-2/3 p-6 gap-8 overflow-y-auto" >
      <AddressBookTable :contacts="addBook" @remove-Contact="removeContact" />
    </div>
  </main>
</template>

