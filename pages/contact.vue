<script setup>
import DsnMap from '@/components/contact/DsnMap.vue';
import DsnFooter from '@/components/footer/DsnFooter.vue';
</script>

<template>

    <Head>
        <Title>Contact</Title>
    </Head>

    <Layout>
        <!-- ========== Header Normal=============== -->
        <HeaderNormal contentClass="container" subTitle="" :linkTo="$route.path" linkName="See More Works">
            <template v-slot:title>
                ¿TIENES UN PROYECTO EN MENTE?
            </template>
            <template v-slot:string>
                Conversemos sobre cómo podemos diseñar y fabricar la solución a tu medida. Contáctanos y hagámoslo realidad.
            </template>
        </HeaderNormal>
        <!-- ========== End Header Normal ========== -->

        <!-- ========== Contact  =================== -->
        <contactForm>
            <template v-slot:form_title>SI TIENES UNA PREGUNTA POR FAVOR CONTÁCTANOS</template>
            <template v-slot:address_title>HEAD OFFICE:</template>
            <template v-slot:address>El-Mahalla El-Kubra37<br>1776 Damietta Egypt</template>
            <template v-slot:phones_title>Phones:</template>
            <template v-slot:phones>
                <NuxtLink to="tel:+1850344066">+1 (850) 344 066</NuxtLink>
            </template>
            <template v-slot:email_title>Write Us:</template>
            <template v-slot:email>
                <NuxtLink to="mailto:info@dsngrid.com">info@dsngrid.com</NuxtLink>
            </template>
        </contactForm>
        <!-- ========== End Contact  =============== -->

        <!-- ========== Map  ======================= -->
        <DsnMap
            mapKey="AIzaSyDMyAS2jdzj-vdgBIFaIStYOWJtSlghndg"
            :zoom="12"
            height="80vh"
            :defaultCenter="{ lat: 13.730089, lng: -89.210031 }"
        />
        <!-- ========== End Map  =================== -->

        <!-- ========== Footer ===================== -->
        <DsnFooter :animateContent="false" />
        <!-- ========== End Footer ================= -->

    </Layout>
</template>
