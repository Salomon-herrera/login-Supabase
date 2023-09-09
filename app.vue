<script setup lang="ts">
const user = useSupabaseUser()
</script>

<template>
    <div>
        <template v-if="!user">
            <NuxtLink to="/login"></NuxtLink>
        </template>
        <template v-else>
            <NuxtLink to="/protected"> Esta es la Paguina de Administracion</NuxtLink>
        </template>
        <NuxtPage />

    </div>
</template>
