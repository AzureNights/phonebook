<template>
    <form v-on:submit.prevent="addItem">

        <h1>Add Contact</h1>

        <p>Name: <input type="text" required v-model="contactName"></p>
        <p>Tel: <input type="number" required v-model="contactNumber"></p>
        <p>Email: <input type="text" required v-model="contactEmail"></p>
        <p>Address: <input type="text" required v-model="contactAdd"></p>
        <button type="submit">Add Contact</button>

    </form>

    <!-- <h3>Contacts</h3>
    <ol>
        <li v-for="item in addBook">{{ ccontact }}</li>


    </ol> -->
</template>

<script>
export default {
    data() {
        return {
            contactName: '',
            contactNumber: '',
            contactEmail: '',
            contactAdd: '',
            addBook: [
                { name: 'Amy', number: 999, email: 'gg@gg.com', address: '1 GG Street' }
            ]
        }
    },

    methods: {
        addItem() {


            console.log('Name:', this.contactName)
            console.log('Tel:', this.contactNumber)
            console.log('Email:', this.contactEmail)
            console.log('Address:', this.contactAdd)

            this.contactName = ''
            this.contactNumber = ''
            this.contactEmail = ''
            this.contactAdd = ''

        }
    },

}
</script>