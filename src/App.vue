<script setup lang="ts">
import { computed } from 'vue'
import Login from './components/Login.vue'
import Navbar from './components/Navbar.vue'
import { useUserDetails } from './composables/useUserDetails'

const user = useUserDetails()
const loggedIn = computed(() => user.value?.role === 'Administrator')
</script>

<template>
	<div class="root">
		<div v-if="loggedIn">
			<Navbar />
			<RouterView />
		</div>
		<Login v-else />
	</div>
</template>

<style scoped>
.root {
	width: 100%;
}
</style>
