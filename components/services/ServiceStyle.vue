<script setup>
import LinkAngle from "@/components/links/LinkAngle.vue"
const props = defineProps({
    data: Array,
    masonry: Boolean,
    center: Boolean,
    counter: Boolean,
    titleClass: String,
    haveButton: Boolean,
    serviceItemClass: String,
    serviceInnerClass: String,
    iconsize: String,
    fadeUp: { type: Boolean,default: false },
});
const { $Isotope } = useNuxtApp();
const isoServices = ref(null);
onMounted(() => {
    if (props.masonry)
        setTimeout(() => { isoServices.value = new $Isotope(isoServices.value?.querySelector('.dsn-service'),{ itemSelector: '.grid-item' }); },500)

});
</script>

<template>
    <div ref="isoServices" class="container section-margin">
        <slot name="title" />
        <div
            :class="['icon-top dsn-icon-theme-color',props.center ? 'text-center' : null,props.counter ? 'list-with-number' : null]">
            <div class="dsn-service d-grid grid-lg-3 grid-sm-2"
                :class="props.masonry ? 'dsn-masonry-grid dsn-masonry-grid-2 dsn-isotope' : null"
                :data-dsn-iconsize="props.iconsize">
                <div v-for="(item,index) in props.data" :key="index"
                    :class="['dsn-up service-item p-relative grid-item style-box',props.serviceItemClass]">
                    <div :class="['service-item-inner number-item h-100',props.serviceInnerClass ? props.serviceInnerClass : null]"
                        :data-fade-up="props.fadeUp">
                        <!-- <div class="dsn-icon">
                            <NuxtImg format="webp" :src="item.svgLight" />
                        </div> -->
                        <div class="service-content p-relative">
                            <h4 :class="['service_title title-block', props.titleClass]" v-html="item.title"></h4>
                            <div class="service_description mt-20 max-w570 dsn-auto">
                                <p v-html="item.string"></p>
                            </div>
                            <!-- <LinkAngle v-if="item.link && props.haveButton" classColor="section" linkName="LEARN MORE"
                                :linkTo="item.link" iconPosition="right" /> -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<style>
.service_description ul {
    list-style-type: none; /* Quita los puntos por defecto */
    padding-left: 0;
    margin-left: 0;
}
.service_description li {
    position: relative;
    padding-left: 1.2em; /* Espacio para el punto */
    margin-bottom: 8px;
}
.service_description li::before {
    content: "•";
    position: absolute;
    left: 0;
    color: #050505; /* Color de tu SVG */
}
</style>



