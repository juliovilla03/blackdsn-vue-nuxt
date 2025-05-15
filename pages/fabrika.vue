<script setup>

import data_InBox from "@/api/box-info/box-info.json";
import data_Portf from "@/api/portfolio/portfolio.json";
import data_Portf_2 from "@/api/portfolio/portfolio2.json";
import data_blogs from "@/api/blog/blog.json";
import data_Serve from "@/api/services/service.json";
import data_IServ from "@/api/services/service-icon.json";
import data_Teste from "@/api/testimonials/testimonials.json";
import data_Brand from "@/api/brands/brand-one.json";
import SectionTitle from "@/components/title/SectionTitle.vue";
import SectionTitleGrid from "@/components/title/SectionTitleGrid.vue";
import LinkDefualt from "@/components/links/LinkDefualt.vue";
import LinkAngle from "@/components/links/LinkAngle.vue";
import ServiceIcon from "@/components/services/ServiceIcon.vue";
import ServiceStyle from "@/components/services/ServiceStyle.vue";
import BoxImage from "@/components/box-image/BoxImage.vue";
import BoxInfo from "@/components/box-info/BoxInfo.vue";
import BoxInfoList from "@/components/box-info/BoxInfoList.vue";
import BoxInfoItem from "@/components/box-info/BoxInfoItem.vue";
import BlogSwiper from "@/components/blog/BlogSwiper.vue";
import Testimonials from "@/components/testimonials/Testimonials.vue";
import BrandOne from "@/components/brand/BrandOne.vue";
import DsnFooter from "@/components/footer/DsnFooter.vue";
import SiteLogo from "@/components/logo/SiteLogo.vue";
</script>

<template>

	<Head>
		<Title>FABRIKA</Title>
	</Head>

	<Layout>
		<!-- ========== Slider Parallax ========== -->
			<PortfolioSlider :data="data_Portf.slice(0, 4)" setStyle="padding-h" contentStyle="end-between" hasDescription
				linkDefualt :webgel="true" :webgelOptions="{
					displacement: 'images/displacement/7.jpg',
					speedIn: 3.5,
				}" :optionSlider="{ direction: 'horizontal' }" :swiperOptions="{
				allowTouchMove: true,
				watchSlidesProgress: true,
				grabCursor: true,
				mousewheel: false,
				speed: 500,
			}" />
		<!-- ========== End Slider Parallax ========== -->

		<!-- ========== Service Icon Left ========== -->
		<ServiceIcon :data="data_IServ" />
		<!-- ========== End Service Icon Left ========== -->

		<!-- ========== About Section One ========== -->
		<AboutOne class="section-padding background-section" bgMask="background-main"
			imageOneSrc="images/About/aboutus.png">
			<template v-slot:moveTitle>¿QUIÉNES </template>
			<template v-slot:centerTitle> SOMOS?</template>
			<template v-slot:description>
				<div class="caja-bottom">
					<p>Fabrika Global es un taller de fabricación especializado en el diseño y producción de piezas en libra de vidrio, estructuras metálicas y soluciones industriales.</p><br>
					<p>Con más de 40 años de experiencia, hemos desarrollado proyectos en diversas industrias, incluyendo el entretenimiento, la arquitectura, la hotelería y el sector náutico.</p><br>    
					<p>Fabrika Marine, nuestra división especializada en el sector náutico, se dedica a la fabricacióny reparación de embarcaciones, componentes marinos y accesorios en fibra de vidrio y aluminio. A través de procesos innovadores, garantizamos durabilidad, resistencia y acabados de primer nivel en cada proyecto.</p><br>
					<p>Nuestro compromiso es ofrecer soluciones personalizadas, utilizando materiales de alta calidad y tecnología avanzada, adaptándonos a las necesidades específicas de cada cliente.</p>    
				</div>
			</template>
			<template v-slot:button>
				<LinkAngle classColor="main" linkName="ABOUT US" linkTo="" style="visibility: hidden"/> <!-- linkTo="/about-us"  -->
			</template>
		</AboutOne>
		<!-- ========== About Section One ========== -->

		<!-- ========== Service ========== -->
		<ServiceStyle :data="data_Serve.slice(0,3)" fadeUp counter titleClass="border-bottom pb-20 mb-20"
			serviceInnerClass="border-style" iconsize="80px" masonry :center="false" haveButton>
			<template v-slot:title>
				<SectionTitleGrid grid btnBackground="background-section" beforeStyle="circle-before"
					subTitle="divisiones" title="<span style='font-size: 36px;'>servicios</span><b style='font-size: 36px;'> principales</b>" />
			</template>
		</ServiceStyle>
		<!-- ========== End Service ========== -->

		<!-- ========== About Section One ========== -->
		<BoxInfo imageSrc="images/BoxInfo/CarteraClientes.png">
			<template v-slot:title>
				<SectionTitle subTitle="cartera de clientes" title="<b>clientes</b> y <br>proyectos<br> destacados"
					beforeStyle="circle-before" :spaceDown="false" />
			</template>
			<template v-slot:string>
				Hemos trabajado con diversas empresas y clientes en múltiples sectores, entregando productos de alta calidad y presición. Nuestro portafolio incluye colaboraciones con:
				<span class="d-block mt-10"></span>
			</template>
			<BoxInfoList>
				<BoxInfoItem v-for="(item,index) in data_InBox" :key="index" :item="item.text" />
			</BoxInfoList>
			<LinkDefualt linkClass="background-main" :iconAwesome="['fas','angle-right']" popup linkName="VER MÁS"
				linkTo="#" parallax /> <!-- linkTo="/portfolio/style-6/headphones" -->
		</BoxInfo>
		<!-- ========== End About Section One ========== -->

		<!-- ========== Portfolio ========== -->
		<PortfolioSwiper :data="data_Portf_2.slice(0, 3)" setStyle="classic" haveOverlayBG allowPrevButton mode
			allowNextButton allowPagination grabCursor loop parallax :centeredSlides="false"
			:desktop="{ slidesPerView: 2.5, spaceBetween: 30, centeredSlides: false }"
			:tablet="{ spaceBetween: 30, slidesPerView: 2, centeredSlides: false }"
			:mobile="{ spaceBetween: 30, slidesPerView: 1, centeredSlides: false }" :speed="1200" watchSlidesProgress
			>
			<template v-slot:title>
				<SectionTitleGrid grid class="container" btnBackground="background-main" beforeStyle="circle-before"
					subTitle="nuestro trabajo" title="<b>portfolio </b><br> de proyectos" linkTo="#"
					linkName="ver todo" /> <!-- linkTo="/work/work-list-1" -->
			</template>
		</PortfolioSwiper>
		<!-- ========== End Portfolio ========== -->

		<!-- ========== background Box Image ========== -->
		<!-- <BoxImage imageSrc="images/about-4.jpg">
			<h3 class="title-h2">
				Need help with professional <br />photography?
				<b>Let's work together!</b>
			</h3>
			<p class="mt-30 max-w570">
				In my work, I try to find the right balance between form and function.
				From technical drawings, all the way to the photographic renders, and the
				actual representations of my work as a designer, my philosophy is that of
				simplicity.
				<span class="mb-10 d-block"></span>
				At the same time, my style is distinctly mine – uncluttered, with clean
				shapes and modern space-saving solutions.
			</p>
			<LinkDefualt linkClass="background-section" :iconAwesome="['far','envelope-open']" popup
				linkName="CONTACT US" linkTo="/contact" parallax />
		</BoxImage> -->
		<!-- ========== End background Box Image ========== -->

		<!-- ========== testimonials ========== -->
		<!-- <Testimonials :data="data_Teste" :stringLine="1" haveOverlayBG Pagination
			className="section-padding background-section" slideClass="border-style" :desktop="{ slidesPerView: 2 }"
			:tablet="{ slidesPerView: 2 }" :mobile="{ slidesPerView: 1 }" grabCursor :centeredSlides="false"
			spaceBetween="30" loop :speed="1200">
			<template v-slot:title>
				<SectionTitleGrid grid btnBackground="background-main" beforeStyle="circle-before" subTitle="advantages"
					title="What People <b>ARE <br>SAYING</b>" linkTo="/contact" linkName="GET STARTED NOW" />
			</template>
		</Testimonials> -->
		<!-- ========== End testimonials ========== -->

		<!-- ========== Stories ========== -->
		<!-- <BlogSwiper setStyle="normal" :data="data_blogs" haveOverlayBG allowPrevButton allowNextButton allowPagination
			grabCursor parallax loop :speed="1200" :desktop="{ slidesPerView: 2.5, spaceBetween: 30 }"
			:tablet="{ slidesPerView: 2, spaceBetween: 30 }" :mobile="{ slidesPerView: 1, spaceBetween: 30 }">
			<template v-slot:title>
				<SectionTitleGrid grid class="container" btnBackground="background-section" beforeStyle="circle-before"
					subTitle="advantages" title="What People <b>ARE <br>SAYING</b>" linkTo="/blog/stories"
					linkName="GET STARTED NOW" />
			</template>
		</BlogSwiper> -->
		<!-- ========== End Stories ========== -->

		<!-- ========== Brand ========== -->
		<BrandOne :data="data_Brand.slice(0,8)" boxStyle="1" class="background-section section-padding">
			<template v-slot:number>40</template>
			<template v-slot:description><h4>AÑOS DE <br />EXPERIENCIA</h4></template>
		</BrandOne>
		<!-- ========== End Brand ========== -->

		<!-- ========== Footer ============== -->
		<DsnFooter containerContent animate />
		<!-- ========== End Footer ========== -->
	</Layout>
</template>
