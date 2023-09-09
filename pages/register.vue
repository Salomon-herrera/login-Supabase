<script setup lang="ts">
definePageMeta({
    middleware: 'unauthenticated'
});

const supaAuth = useSupabaseClient().auth

const credentials = reactive({
    email: '',
    password: ''
})

const register = async () => {
    const { error } = await supaAuth.signUp(credentials)
    if (error) {
        alert(error.message);
    } else {
        return navigateTo('/')
    }
}
</script>



<template>
    <div>
        <h1>Register Page</h1>
        <form @submit.prevent="register">
            <input v-model="credentials.email" type="email" placeholder="Email" />
            <input v-model="credentials.password" type="password" placeholder="Password" />
            <button type="submit">Register</button>
        </form>
    </div>
</template>
