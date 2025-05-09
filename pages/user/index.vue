<!-- <template>
    <div>
        <div class="badge-base LI-profile-badge" data-locale="en_US" data-size="medium" data-theme="dark"
            data-type="HORIZONTAL" data-vanity="wajahatullah-sakhi-2952b2251" data-version="v1"><a
                class="badge-base__link LI-simple-link"
                href="https://pk.linkedin.com/in/wajahatullah-sakhi-2952b2251?trk=profile-badge">Wajahatullah Sakhi</a>
        </div>

    </div>
</template> -->

<!-- <script setup>
definePageMeta({
    layout: 'user'
})

</script> -->

<style></style>

<script setup>
definePageMeta({
    layout: 'user',
    middleware: 'authenticated',
})

const { user, clear: clearSession } = useUserSession()

async function logout() {
    await clearSession()
    await navigateTo('/')
}
</script>

<template>
    <div>
        <button @click="logout">Logout</button>
    </div>
</template>