<template>
    <div
        class="flex items-center max-[500px]:justify-center h-full max-md:mt-3"
    >
        <div class="flex items-center h-full">
            <button
                @click="decCount"
                class="group rounded-l-xl px-5 py-[12px] border border-gray-200 flex items-center justify-center shadow-sm shadow-transparent transition-all duration-500 hover:bg-gray-50 hover:border-gray-300 hover:shadow-gray-300 focus-within:outline-gray-300"
            >
                <svg
                    class="stroke-gray-900 transition-all duration-500 group-hover:stroke-black"
                    xmlns="http://www.w3.org/2000/svg"
                    width="22"
                    height="22"
                    viewBox="0 0 22 22"
                    fill="none"
                >
                    <path
                        d="M16.5 11H5.5"
                        stroke=""
                        stroke-width="1.6"
                        stroke-linecap="round"
                    />
                    <path
                        d="M16.5 11H5.5"
                        stroke=""
                        stroke-opacity="0.2"
                        stroke-width="1.6"
                        stroke-linecap="round"
                    />
                    <path
                        d="M16.5 11H5.5"
                        stroke=""
                        stroke-opacity="0.2"
                        stroke-width="1.6"
                        stroke-linecap="round"
                    />
                </svg>
            </button>
            <input
                type="text"
                @input="changeQuantity"
                v-model="count"
                class="border-y border-gray-200 outline-none text-gray-900 font-semibold text-lg w-full max-w-[73px] min-w-[60px] placeholder:text-gray-900 py-[9px] text-center bg-transparent"
            />
            <button
                @click="incCount"
                class="group rounded-r-xl px-5 py-[12px] border border-gray-200 flex items-center justify-center shadow-sm shadow-transparent transition-all duration-500 hover:bg-gray-50 hover:border-gray-300 hover:shadow-gray-300 focus-within:outline-gray-300"
            >
                <svg
                    class="stroke-gray-900 transition-all duration-500 group-hover:stroke-black"
                    xmlns="http://www.w3.org/2000/svg"
                    width="22"
                    height="22"
                    viewBox="0 0 22 22"
                    fill="none"
                >
                    <path
                        d="M11 5.5V16.5M16.5 11H5.5"
                        stroke=""
                        stroke-width="1.6"
                        stroke-linecap="round"
                    />
                    <path
                        d="M11 5.5V16.5M16.5 11H5.5"
                        stroke=""
                        stroke-opacity="0.2"
                        stroke-width="1.6"
                        stroke-linecap="round"
                    />
                    <path
                        d="M11 5.5V16.5M16.5 11H5.5"
                        stroke=""
                        stroke-opacity="0.2"
                        stroke-width="1.6"
                        stroke-linecap="round"
                    />
                </svg>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            count: 1,
        };
    },
    props: {
        quantity: {
            type: Number,
            default: 1,
        },
    },
    methods: {
        incCount() {
            this.count++;
            this.$emit("change", this.count);
        },
        decCount() {
            if (this.count > 1) {
                this.count--;
                this.$emit("change", this.count);
            }
        },
        changeQuantity() {
            this.$emit("change", this.count);
        },
    },
    mounted() {
        this.count = this.quantity;
    },
};
</script>
