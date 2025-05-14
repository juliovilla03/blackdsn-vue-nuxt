<script setup>
const props = defineProps({
	imageOneSrc: String,
	imageTwoSrc: String,
	bgMask: String,
	smTitleBlock: Boolean
});
</script>

<template>
	<section class="about-section about-one p-relative">
		<div class="p-relative container">
			<div :class="['bg-mask w-70 h-70 v-middle',props.bgMask]" style="margin-top: 60px;"></div>
			<div class="d-grid grid-md-2">
				<div class="box-info">
					<h2 class="title">
						<span class="letter-stroke d-block" v-if="$slots.moveTitle" data-move-this="true"
							data-dsn-animate='{"trigger":{},"from":{"paddingLeft":"20%"},"to":{"paddingLeft":"-20%"}}'>
							<slot name="moveTitle" />
						</span>
						<span v-if="$slots.centerTitle" data-move-this="true"
						data-dsn-animate='{"trigger":{},"from":{"paddingLeft":"-5%"},"to":{"paddingLeft":"5%"}}'>
							<slot name="centerTitle" />
						</span>
						<span class="text-right w-100" v-if="$slots.lastTitle">
							<slot name="lastTitle" />
						</span>
					</h2>
					<div class="d-grid grid-half-1 align-items-center mt-10">
						<slot name="button" />
						<div class="p-large text-right" v-if="$slots.description">
							<p :class="['max-w350',props.smTitleBlock ? 'sm-title-block' : null]">
								<slot name="description" />
							</p>
						</div>
					</div>
				</div>
				<div class="box-img" v-if="props.imageOneSrc">
					<NuxtImg format="webp" class="cover-bg-img" :src="props.imageOneSrc" alt="about" />
				</div>
			</div>
			<div class="p-relative box-img-bottom w-90 hv-30" style="margin-left: 138px;" v-if="props.imageTwoSrc">
				<NuxtImg format="webp" class="cover-bg-img" :src="props.imageTwoSrc" alt="about" />
			</div>
		</div>
	</section>
</template>

<style lang="scss">
@import "@/assets/styles/variables-site/colors";
@import "@/assets/styles/mixins/utilities";
@import "./global_style/about-section";

.about-one {
	.box-info {
		margin-bottom: 30px;
		position: relative;
		z-index: 1;
	}

	@include media_768(min) {
		.box-info .title .text-right {
			padding-left: 50%;
		}

		.box-img {
			position: relative;

			img {
				position: absolute;
				height: 80%;
				margin-top: 150px;
			}
		}

		.box-img-bottom {
			padding-right: 60px;
		}
	}

	@include media_768() {
		.box-info {
			.d-grid {
				.dsn-def-btn {
					order: 2;
				}

				p {
					order: 1;
					text-align: left;
					margin-top: 10px;
				}
			}

			.title {
				font-size: 55px;
				line-height: inherit;
				margin-left: 40px;

				span {
					display: inline-block;
					width: auto;
					text-align: left;
				}
			}
		}

		

		.bg-mask {
			display: none;
		}
	}
	
	.caja-bottom{
		margin-bottom: 180px;

		@include media_768() {
    	margin-bottom: 0px; // Nuevo valor para teléfonos
  		}
	}
}
</style>
