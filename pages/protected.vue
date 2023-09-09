<script setup lang="ts">
definePageMeta({
    middleware: 'authenticated'
})

const supaAuth = useSupabaseClient().auth

const logout = async () => {
    const { error } = await supaAuth.signOut()
    if (error) {
        alert(error.message)
    } else {
        return navigateTo('/login')
    }
}
</script>

<template>
    <h1> Aqui es donde esta la pega</h1>

    <div class="absolute top-4 right-10 h-15 w-15">
        <button @click="logout"
            class="text-white bg-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-teal-600 dark:hover:bg-teal-700 dark:focus:ring-teal-800">Logout
        </button>
    </div>
</template>
