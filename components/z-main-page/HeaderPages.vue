<script setup>
import { elScrollDown } from "@/hooks/plugin.js";
import LinkNormal from "@/components/links/LinkNormal.vue";
</script>

<template>
	<header class="p-relative pt-header background-theme">
		<div class="hero-content text-center">
			<p>Soluciones a la medida</p>
			<h1 class="title-head mt-20 text-upper">
				INNOVACIÓN
				<br />
				EN FIBRA Y METAL
			</h1>
			<p class="max-w570 mt-20">
				Transformamos ideas en realidad con calidad y precisión.
			</p>
			<LinkNormal :linkTo="$route.path" @click="elScrollDown('demospage')" linkName="Get Started Now" center
				parallax background="background-section" />
		</div>
		<div class="mt-section hero-image dsn-container">
			<NuxtImg format="webp" class="w-100" src="images/preview/demo.png" alt="" />
		</div>
	</header>
</template>
