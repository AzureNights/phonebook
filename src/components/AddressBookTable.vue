<template>
    <div class="w-full overflow-hidden rounded-lg border border-stone-200">
        <table class="w-full">
            <thead class="border-b border-stone-200 bg-stone-100 text-sm font-medium text-stone-600 dark:bg-surface-dark">
                <tr>
                    <th class="px-2.5 py-2 text-start font-medium">Name</th>
                    <th class="px-2.5 py-2 text-start font-medium">Telephone Number</th>
                    <th class="px-2.5 py-2 text-start font-medium">Email Address</th>
                    <th class="px-2.5 py-2 text-start font-medium">Address</th>
                </tr>
            </thead>

            <tbody class="group text-sm text-stone-800 dark:text-white">
                <tr v-for="(contact, index) in contacts" :key="index" class="border-b border-stone-200 last:border-0">
                    <td class="p-3">{{ contact.name }}</td>
                    <td class="p-3">{{ contact.number }}</td>
                    <td class="p-3">{{ contact.email }}</td>
                    <td class="p-3">{{ contact.address }}</td>
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



