<script setup>
import { store } from "@/store/store";
const props = defineProps({ click: Function, name: String });
</script>

<template>
	<div class="main-logo main-brand" @click="props.click()">
		<NuxtLink to="#" v-if="store.colorPage == 'v-dark'">
			<NuxtImg class="logo-light" src="images/logoFK2.png" alt="logo" width="auto" height="50"></NuxtImg>
		</NuxtLink>
		<NuxtLink to="#" v-if="store.colorPage == 'v-light'">
			<NuxtImg format="webp" class="logo-light" src="images/logoFK.png" alt="logo" width="auto" height="40"></NuxtImg>
		</NuxtLink>
		{{ props.name }}
	</div>
</template>
