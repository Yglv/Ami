<template>
    <button
        @click="addInCart"
        title=""
        class="bg-green-700 hover:bg-green-500 text-lg text-white mt-4 sm:mt-0 bg-primary-700 hover:bg-primary-800 0 font-medium rounded-lg px-5 py-2.5 flex items-center justify-center"
        role="button"
    >
        <svg
            class="w-9 h-9 -ms-2 me-2"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="none"
            viewBox="0 0 24 24"
        >
            <path
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 4h1.5L8 16m0 0h8m-8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm.75-3H7.5M11 7H6.312M17 4v6m-3-3h6"
            />
        </svg>

        <span class="pl-4">Добавить в корзину</span>
    </button>
</template>

<script>
export default {
    methods: {
        addInCart() {
            this.$emit("addInCart");
        },
    },
};
</script>
