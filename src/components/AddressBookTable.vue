<template>
    <div class="w-full max-w-screen-md overflow-y-auto max-h-130 rounded-lg border border-stone-200 ">
        <table class="w-full">
            <thead class="border-b border-stone-200 bg-stone-100 text-sm font-medium text-stone-600 dark:bg-surface-dark">
                <tr>
                    <th class="px-2.5 py-2 text-center font-medium">Name</th>
                    <th class="px-2.5 py-2 text-center font-medium">Telephone Number</th>
                    <th class="px-2.5 py-2 text-center font-medium">Email Address</th>
                    <th class="px-2.5 py-2 text-center font-medium">Address</th>
                    <th class="px-2.5 py-2 text-center font-medium">Delete</th>
                </tr>
            </thead>

            <tbody class="group text-sm text-stone-800 dark:text-white">
                <tr v-for="(contact, index) in contacts" :key="index" class="border-b border-stone-200 last:border-0">
                    <td class="p-3 text-center">{{ contact.name }}</td>
                    <td class="p-3 text-center">{{ contact.number }}</td>
                    <td class="p-3 text-center">{{ contact.email }}</td>
                    <td class="p-3 text-center">{{ contact.address }}</td>
                    <td class="p-3 text-center">
                        <button @click="$emit('remove-contact', index)"
                        class="bg-red-500 hover:bg-red-700 text-white px-2.5 py-1.5 rounded "> X

                        </button>
                    </td>
                </tr>
            </tbody>
         </table>
    </div>
</template>

<script>
export default {
    props: {
        contacts: {
            type: Array,
            required: true
        }
    }
};
</script>



