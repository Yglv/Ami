<template>
    <layout>
        <section>
            <div class="w-full" scroll-region></div>
        </section>
        <HeroSection />
        <section>
            <ProductList v-bind:details="details" />
            <LogoClouds />
            <News />
        </section>
    </layout>
</template>

<script>
import LogoClouds from "./LogoClouds.vue";
import ProductList from "./ProductList.vue";
import News from "@/Shared/News.vue";

import HeroSection from "@/Pages/User/HeroSection.vue";

export default {};
</script>

<script setup>
defineProps({
    details: Object,
});
</script>
