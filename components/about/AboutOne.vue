<script setup>
const props = defineProps({
	imageOneSrc: String,
	imageTwoSrc: String,
	bgMask: String,
	smTitleBlock: Boolean
});
</script>

<template>
	<section class="about-section about-one p-relative device-frame">
		<div class="p-relative container">
			<div class="d-grid content-grid">
				<div class="text-content-box">
					<h2 class="title">
						<span class="letter-stroke d-block" v-if="$slots.moveTitle" data-move-this="true"
							data-dsn-animate='{"trigger":{},"from":{"paddingLeft":"20%"},"to":{"paddingLeft":"-20%"}}'>
							<slot name="moveTitle" />
						</span>
						<span v-if="$slots.centerTitle" data-move-this="true" 
						data-dsn-animate='{"trigger":{},"from":{"paddingLeft":"-10%"},"to":{"paddingLeft":"10%"}}'>
							<slot name="centerTitle"/>
						</span>
					</h2>
					<div class="description-content" v-if="$slots.description">
						<p :class="['description-text',props.smTitleBlock ? 'sm-title-block' : null]">
							<slot name="description" />
						</p>
					</div>
				</div>
				<div class="images-container">
					<div class="bottom-image" v-if="props.imageTwoSrc">
						<NuxtImg format="webp" class="cover-bg-img" :src="props.imageTwoSrc" alt="about structure" />
					</div>
					<div class="top-image" v-if="props.imageOneSrc">
						<NuxtImg format="webp" class="cover-bg-img" :src="props.imageOneSrc" alt="about" />
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<style lang="scss">
@import "@/assets/styles/variables-site/colors";
@import "@/assets/styles/mixins/utilities";
@import "./global_style/about-section";

.about-one {
	padding: 20px;
	
	// Estilo para el contenedor principal
	&.device-frame {
		border-radius: 15px;
		overflow: hidden;
		background-color: none;
		/* max-width: 1080px; */
		margin: 0 auto;
		position: relative;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
	}

	.content-grid {
		display: grid;
		grid-template-columns: 55% 45%;
		gap: 20px;
		margin-left: 100px;
		margin-bottom: 50px;
	}
	
	.text-content-box {
		background-color: white;
		padding: 30px;
		border-radius: 8px;
		position: relative;
		z-index: 1;
		margin-left: 60px;

		.title {
			/* margin-bottom: 10px; */
			font-size: 5rem;
			line-height: 1; // Reduce el espacio vertical entre líneas
			margin-bottom: 20px;
			
			.letter-stroke {
				color: transparent;
				-webkit-text-stroke: 1px #000;
				font-weight: 400;
				font-size: 5rem;
			}
			
			.text-left {
				text-align: left;
				font-size: 4rem;
				font-weight: bold;
				line-height: 1;
				margin-top: -10px;
			}
		}
		
		.description-content {
			/* margin-top: 20px; */
			width: 70%;
			
			.description-text {
				line-height: 1.6;
				font-size: 12px;
				width: 350px;
				/* margin-bottom: 20px; */
			}
		}
	}

	.images-container {
		display: flex;
		flex-direction: column;
		position: relative;
		height: 100%;
		
		.top-image {
			height: 55%;
			overflow: hidden;
			border-radius: 8px;
			position: absolute;
			top: 40px;
			left: -100px; // Desplazada a la izquierda
			right: 0;
			width: 100%;
			z-index: 1;
			
			img {
				width: 70%;
				height: 100%;
				object-fit: cover;
			}
		}
		
		.bottom-image {
			height: 55%;
			overflow: hidden;
			border-radius: 8px;
			position: absolute;
			top: 57%;
			bottom: 0;
			left: -150px; // Desplazada a la izquierda
			width: 100%;
			z-index: 2; // Mayor z-index para estar por encima
			margin-bottom: 0;
			
			img {
				width: 70%;
				height: 90%;
				object-fit: cover;
			}
		}
	}

	@include media_768(min) {
		.title .letter-stroke {
			font-size: 4rem;
		}
		
		.title .text-left {
			font-size: 5rem;
		}
	}

	@include media_768() {
		.content-grid {
			grid-template-columns: 1fr;
		}
		
		.text-content-box {
			order: 1;
		}
		
		.images-container {
			order: 2;
			height: 500px;
			margin-top: 20px;
			
			.top-image {
				position: relative;
				height: 250px;
				margin-top: 20px;
			}
			
			.bottom-image {
				position: relative;
				height: 250px;
				left: 0;
				margin-bottom: 0;
			}
		}
		
		.title {
			font-size: 30px;
			line-height: inherit;
			
			.letter-stroke {
				font-size: 2.5rem;
			}
			
			.text-left {
				font-size: 3rem;
			}
			
			span {
				display: inline-block;
				width: auto;
				text-align: left;
			}
		}
	}
}
</style>