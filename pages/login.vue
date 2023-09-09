<script setup lang="ts">
definePageMeta({
    middleware: 'unauthenticated'
});

const supaAuth = useSupabaseClient().auth

const credentials = reactive({
    email: '',
    password: ''
})

const login = async () => {
    const { error } = await supaAuth.signInWithPassword(credentials)
    if (error) {
        alert(error.message);
    } else {
        return navigateTo('/')
    }
}
</script>





<template>
    <body class="bg-slate-100">

        <div class="flex h-screen justify-center items-center">


            <form @submit.prevent="login" class="mb-6 space-y-2 flex flex-col items-center">
                <svg class="flex h-screen justify-center w-10 h-10 text-gray-400 -left-1" fill="currentColor"
                    viewBox="0 0 20 20" xmlns="https://www.svgrepo.com/show/530478/bank.svg">
                    <path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd">
                    </path>
                </svg>
                <input v-model="credentials.email" type="email"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    placeholder="Email" />
                <input v-model="credentials.password" type="password"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    required placeholder="Password" />
                <button type="submit"
                    class="text-white bg-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-teal-600 dark:hover:bg-teal-700 dark:focus:ring-teal-800">Login</button>
            </form>
        </div>
    </body>
</template>
