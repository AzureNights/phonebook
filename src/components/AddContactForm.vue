<template>

    <div class="flex gap-8 p-6">

        <form v-on:submit.prevent="addContactToBook" class="max-w-md mx-auto p-6 bg-white rounded-lg shadow-md space-y-4">

            <h1 class="text-xl font-semibold mb-4 text-center">My Little Phone Book</h1>

            <br />

            <!-- <p>Name: <input type="text" required v-model="contactName"></p>
            <p>Tel: <input type="number" required v-model="contactNumber"></p>
            <p>Email: <input type="text" required v-model="contactEmail"></p>
            <p>Address: <input type="text" required v-model="contactAdd"></p> -->

            <div class="w-72 space-y-1">
                <label for="name" class="font-sans antialiased text-sm text-stone-800 dark:text-white font-semibold">Name</label>
                <div class="relative w-full">
                    <input required v-model="contactName" id="name" placeholder="Amy Winehouse" type="text" class="w-full aria-disabled:cursor-not-allowed outline-none focus:outline-none text-stone-800 dark:text-white placeholder:text-stone-600/60 ring-transparent border border-stone-200 transition-all ease-in disabled:opacity-50 disabled:pointer-events-none select-none text-sm py-2 px-2.5 ring shadow-sm bg-white rounded-lg duration-100 hover:border-stone-300 hover:ring-none focus:border-stone-400 focus:ring-none peer" />
                </div>
            </div>

            <br />

            <div class="w-72 space-y-1"> 
                <!-- change the div class name for each one ? -->
                <label for="tel" class="font-sans antialiased text-sm text-stone-800 dark:text-white font-semibold">Telephone Number</label>
                <div class="relative w-full">
                    <input required v-model="contactNumber" id="number" placeholder="12345678" type="number" class="w-full aria-disabled:cursor-not-allowed outline-none focus:outline-none text-stone-800 dark:text-white placeholder:text-stone-600/60 ring-transparent border border-stone-200 transition-all ease-in disabled:opacity-50 disabled:pointer-events-none select-none text-sm py-2 px-2.5 ring shadow-sm bg-white rounded-lg duration-100 hover:border-stone-300 hover:ring-none focus:border-stone-400 focus:ring-none peer" />
                </div>
            </div>

            <br />

            <div class="w-72 space-y-1">
                <label for="email" class="font-sans antialiased text-sm text-stone-800 dark:text-white font-semibold">Email</label>
                <div class="relative w-full">
                    <input required v-model="contactEmail" id="email" placeholder="someone@example.com" type="email" class="w-full aria-disabled:cursor-not-allowed outline-none focus:outline-none text-stone-800 dark:text-white placeholder:text-stone-600/60 ring-transparent border border-stone-200 transition-all ease-in disabled:opacity-50 disabled:pointer-events-none select-none text-sm py-2 px-2.5 ring shadow-sm bg-white rounded-lg duration-100 hover:border-stone-300 hover:ring-none focus:border-stone-400 focus:ring-none peer" />
                </div>
            </div>

            <br />

            <div class="w-72 space-y-1">
                <label for="address" class="font-sans antialiased text-sm text-stone-800 dark:text-white font-semibold">Address</label>
                <div class="relative w-full">
                    <input required v-model="contactAdd" id="address" placeholder="Belle's Castle 123 Disneyland" type="text" class="w-full aria-disabled:cursor-not-allowed outline-none focus:outline-none text-stone-800 dark:text-white placeholder:text-stone-600/60 ring-transparent border border-stone-200 transition-all ease-in disabled:opacity-50 disabled:pointer-events-none select-none text-sm py-2 px-2.5 ring shadow-sm bg-white rounded-lg duration-100 hover:border-stone-300 hover:ring-none focus:border-stone-400 focus:ring-none peer" />
                </div>
            </div>

            <br />
            <br />
            <button type="submit" class="w-full inline-flex items-center justify-center border align-middle select-none font-sans font-medium text-center duration-300 ease-in disabled:opacity-50 disabled:shadow-none disabled:cursor-not-allowed focus:shadow-none text-sm py-2 px-4 shadow-sm hover:shadow-md bg-stone-800 hover:bg-stone-700 relative bg-gradient-to-b from-stone-700 to-stone-800 border-stone-900 text-stone-50 rounded-lg hover:bg-gradient-to-b hover:from-stone-800 hover:to-stone-800 hover:border-stone-900 after:absolute after:inset-0 after:rounded-[inherit] after:box-shadow after:shadow-[inset_0_1px_0px_rgba(255,255,255,0.25),inset_0_-2px_0px_rgba(0,0,0,0.35)] after:pointer-events-none transition antialiased">Add Contact</button>

        </form>

        <!-- To pass the form as a prop to my table -->
        <AddressBookTable :contacts="addBook" />

    </div>
</template>

<script>
export default {
    data() {
        return {
            contactName: '',
            contactNumber: '',
            contactEmail: '',
            contactAdd: '',
        }
    },


    // moved to App.vue - parent file 
    // mounted() {
    //     const savedContacts = localStorage.getItem('addBook');
    //     if (savedContacts) {
    //         this.addBook = JSON.parse(savedContacts)
    //     }
    // },

    methods: {
        addContactToBook() {
            const newContact =  {
                name: this.contactName,
                number: this.contactNumber,
                email: this.contactEmail,
                address: this.contactAdd     
            };

            this.$emit('add-contact', newContact); //to send the info up to the parent 
            this.resetForm()

        },

            resetForm() {
                this.contactName = '';
                this.contactNumber = '';
                this.contactEmail = '';
                this.contactAdd = '';
            }
    }
};
</script>