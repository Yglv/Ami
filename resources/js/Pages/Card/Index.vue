<template>
    <layout>
        <section class="py-8 bg-white md:py-16 dark:bg-gray-900 antialiased">
            <div class="w-full px-4 2xl:px-0">
                <div class="lg:grid px-4 lg:grid-cols-3 lg:gap-8 xl:gap-16">
                    <div class="shrink-0 max-w-md lg:max-w-lg mx-auto">
                        <img
                            v-if="detail.dt_foto.length === 0"
                            class="w-full hidden dark:block"
                            src="https://flowbite.s3.amazonaws.com/blocks/e-commerce/imac-front-dark.svg"
                            alt=""
                        />
                        <img
                            v-else
                            class="w-full dark:hidden"
                            src="../../../../public/build/no-photo--lg.png"
                            alt="#"
                        />
                    </div>

                    <div class="mt-6 sm:mt-8 lg:mt-0">
                        <h1
                            class="text-4xl font-semibold text-gray-900 dark:text-white mb-8"
                        >
                            {{ editTitle(detail.dt_typec) }}
                            {{ detail.dt_invoice }}
                        </h1>
                        <p class="font-normal text-2xl leading-8 text-gray-500">
                            OEM: <strong>{{ detail.dt_oem }}</strong>
                        </p>
                        <p class="font-normal text-2xl leading-8 text-gray-500">
                            CARGO: <strong>{{ detail.dt_cargo }}</strong>
                        </p>
                        <p class="font-normal text-2xl leading-8 text-gray-500">
                            Бренд: <strong>{{ detail.fr_code }}</strong>
                        </p>

                        <div class="mt-4 sm:items-center sm:gap-4 sm:flex">
                            <p
                                class="text-2xl font-extrabold text-gray-900 sm:text-3xl dark:text-white"
                            >
                                BYN 0
                            </p>
                        </div>

                        <div
                            class="mt-6 sm:gap-4 sm:items-center sm:flex sm:mt-8"
                        >
                            <cart-button
                                @click="addInCart"
                                title=""
                                class="bg-green-700 hover:bg-green-500 text-lg text-white mt-4 sm:mt-0 bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 font-medium rounded-lg px-5 py-2.5 dark:bg-primary-600 dark:hover:bg-primary-700 focus:outline-none dark:focus:ring-primary-800 flex items-center justify-center"
                                role="button"
                            >
                            </cart-button>
                        </div>

                        <hr
                            class="my-6 md:my-8 border-gray-200 dark:border-gray-800"
                        />
                    </div>
                    <div
                        v-if="!!isHasDetails()"
                        class="rounded-lg border-2 w-[80%]"
                    >
                        <p class="text-2xl px-4 py-4 text-center border-b-2">
                            <strong>Деталировка</strong>
                        </p>
                        <div class="h-[400px] overflow-y-auto">
                            <detail-list :details="sameDetails" />
                        </div>
                        <!--div class="h-[400px] overflow-y-auto">
                            <div class="flex flex-col">
                                <div class="flex justify-around pt-2">
                                    <p class="text-xl font-bold">Кросс</p>
                                    <p class="text-xl font-bold">Бренд</p>
                                </div>
                                <div class="flex justify-around">
                                    <p></p>
                                    <p></p>
                                </div>
                            </div>
                        </div!-->
                    </div>
                </div>
            </div>
        </section>
    </layout>
</template>

<script>
import axios from "axios";
import { editDetailTitle } from "@/Services/TitleService";

export default {
    created() {
        console.log(this.sameDetails);
    },
    methods: {
        addInCart() {
            axios
                .post("/cart", {
                    id: this.detail[0].dt_id,
                    typec: this.detail[0].dt_typec,
                    invoice: this.detail[0].dt_invoice,
                    cargo: this.detail[0].dt_cargo,
                    fr_code: this.detail[0]._code,
                })
                .then((res) => console.log(res))
                .catch((err) => console.log(err));
        },
        editTitle(str) {
            return editDetailTitle(str);
        },
        isHasDetails() {
            if (
                this.detail.dt_typec === "ГЕНЕРАТОР" ||
                this.detail.dt_typec === "СТАРТЕР"
            ) {
                return true;
            }
            return false;
        },
    },
    created() {
        console.log(this.detail);
    },
};
</script>

<script setup>
import axios from "axios";

defineProps({
    sameDetails: {
        type: Array,
    },
    detail: {
        type: Array,
    },
});
</script>
