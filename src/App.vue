<script setup>
import AddContact from './components/AddContactForm.vue';
import AddressBookTable from './components/AddressBookTable.vue';

</script>

<template>


  <main class="flex flex-row p-10 gap-8 w-350 bg-black left-400">
  


    <div id="form" class="w-1/3 p-2 bg-blue-500">
      <AddContact />

    </div>


    <div id="table" class="w-2/3 p-6 gap-8 bg-cyan-500">

      <AddressBookTable />

    </div>

  </main>
</template>