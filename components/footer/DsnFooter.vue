<script setup>
import { Animate } from "@/hooks/pluginanimations.js";
import SiteLogo from "@/components/logo/SiteLogo.vue";
import LinkDefualt from "@/components/links/LinkDefualt.vue";
import SvgSeparator from "@/components/svg/SvgSeparator.vue";                    //poner como true para animacion
const props = defineProps({ light: Boolean,animate: Boolean,animateContent: { type: Boolean,default: false },containerContent: Boolean,});
const footer = ref(null);
const footerContent = ref(null);
const socialData = [
    {
        name: "Fb",
        link: "#",
        type: "fab",
        iconName: "facebook-f",
    },
    {
        name: "Tw",
        link: "#",
        type: "fab",
        iconName: "x-twitter",
    },
    {
        name: "In",
        link: "#",
        type: "fab",
        iconName: "linkedin-in",
    },
    {
        name: "Ins",
        link: "#",
        type: "fab",
        iconName: "instagram",
    },
];
const footerLinks = [
    { link: "#",name: "INICIO" },/* / */
    { link: "#",name: "QUIÉNES SOMOS" }, /* /work/work-classic-2 */
    { link: "#",name: "SERVICIOS" }, /* /blog/stories */
    { link: "#",name: "CLIENTES" }, /* /about-us */
    { link: "#",name: "PORTFOLIO" }, /* /contact */
    { link: "#",name: "CONTACTO" }
];

onMounted(() => {
    if (!props.animateContent) return;
    new Animate({ start: "top bottom",end: "top " },{ yPercent: -70 },{ yPercent: 0 },footer.value,footerContent.value);
});
</script>

<template>
    <footer ref="footer" id="dsn_footer" :class="['p-relative svg-animate',
        props.light ? 'background-section' : 'background-main',
        props.animate ? 'footer-animate' : ''
    ]">
        <SvgSeparator :light="props.light" />
        <div ref="footerContent"
            :class="['footer-content p-relative mt-section',props.containerContent ? 'container' : null]">
            <div class="container">
                <h2 class="text-center title-h2">
                    <span class="d-block"><b>TRANSFORMAMOS IDEAS EN REALIDAD CON CALIDAD Y PRESICIÓN</b></span>
                </h2>
                <LinkDefualt class="justify-content-center mt-30"
                    :linkClass="props.light ? 'background-main' : 'background-section'"
                    :iconAwesome="['fas','angle-right']" popup linkName="CONTÁCTANOS" linkTo="/contact" parallax /> <!-- linkTo="/contact" -->
            </div>
            <div class="dsn-container pt-60">
                <div class="d-grid grid-lg-4 grid-md-2">
                    <div class="grid-col-1">
                        <div class="dsn-logo main-logo">
                            <SiteLogo height="undefined" width="undefined" />
                        </div>
                        <SocialGroup class="mt-20 dsn-icon-heading-color" :data="socialData" />
                    </div>
                    <div class="grid-col-2">
                        <h4 class="subtitle p-relative line-shape line-shape-after">
                            <span class="background-revere">NAVEGACIÓN</span>
                        </h4>
                        <div class="menu-footer-menu-container">
                            <ul id="menu-footer-menu" class="menu">
                                <li v-if="footerLinks.length > 0" class="menu-item" v-for="(item,index) in footerLinks"
                                    :key="index">
                                    <NuxtLink :to="item.link ? item.link : $route.path" class="effect-ajax">{{ item.name
                                        }}</NuxtLink>
                                </li>
                            </ul>
                        </div>
                    </div>
                    <div class="grid-col-3">
                        <h4 class="subtitle p-relative line-shape line-shape-after">
                            <span class="background-revere">CONTACTO</span>
                        </h4>
                        <div class="col-contact">
                            <p class="over-hidden mt-5">
                                <a class="link-hover" href="mailto:EMAIL@MAIL.COM">&nbsp;EMAIL@MAIL.COM</a>
                            </p>
                            <p class="mt-5">&nbsp;+503 0000 0000</p>
                            <p class="mt-5">&nbsp;+503 0000 0000</p>
                        </div>
                    </div>
                    <div class="grid-col-4">
                        <h4 class="subtitle p-relative line-shape line-shape-after">
                            <span class="background-revere">DIRECCIÓN</span>
                        </h4>
                        <div class="col-address">
                            <p>
                                DIRECCIÓN LINEA 1<br />
                                DIRECCIÓN LINEA 2
                            </p>
                        </div>
                    </div>
                </div>
                <div class="footer-bottom mt-60 pt-30 border-top pb-30 text-center">
                    <p class="over-hidden">
                        © FABRIKA 2025
                        <a href="#0" class="link-hover" target="_blank"></a>
                    </p>
                </div>
            </div>
        </div>
    </footer>
</template>

<style lang="scss">
@import "@/assets/styles/variables-site/fonts";
@import "@/assets/styles/variables-site/colors";
@import "@/assets/styles/mixins/utilities";

#dsn_footer {
    overflow: hidden;

    @include media_575X768 {
        .grid-col-1 {
            grid-column: 1 / 4;
        }
    }

    &.container,
    &.dsn-container {

        .container,
        .dsn-container {
            padding-right: 0;
            padding-left: 0;
        }
    }

    h4.subtitle {
        margin-bottom: 20px;
        display: inline-block;

        span {
            padding: 3px 10px;
            font-size: 16px;
            letter-spacing: 2px;
            font-weight: $font-weight-body;
        }
    }

    ul.menu,
    ul.sub-menu {
        li {
            a {
                font-weight: 600;
                font-size: 11px;
                letter-spacing: 2.5px;
            }

            &:not(:last-child) a {
                margin-bottom: 7px;
            }
        }
    }

    .list-inline-block {

        ul.menu li,
        ul.sub-menu li {
            display: inline-block;

            a {
                margin-bottom: 0;
            }

            &:not(:last-of-type) {
                margin-left: 5px;
            }
        }
    }

    .textwidget {

        &>*,
        & p {
            &:not(:last-child) {
                margin-bottom: 10px;
            }
        }
    }

    .col-contact {
        p {
            font-size: 14px;

            strong {
                color: $heading-color;
            }

            span {
                margin-right: 5px;
                margin-left: 5px;
            }

            a {
                text-transform: none;
            }
        }
    }
}
</style>