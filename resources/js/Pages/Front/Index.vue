<script setup>
import { Head, Link } from "@inertiajs/vue3";
import { onMounted, ref } from "vue";
import { LottieAnimation } from "lottie-web-vue";
import WatermelonJSON from "/public/img/robot.json";

// Menginisialisasi variabel anim sebagai referensi Vue
let anim = ref();

// Menjalankan kode setelah komponen dipasang (mounted)
onMounted(() => {
    // Menunggu 500ms sebelum menjalankan kode berikutnya
    setTimeout(() => {
        // Menggunakan metode goToAndPlay dari animasi Lottie dengan parameter 150
        // untuk memulai animasi pada frame 150, dengan loop (true)
        console.log(anim.value.goToAndPlay(150, true));
        // Memanggil objek anim.value untuk menjalankan animasi Lottie
        anim.value.play();
    }, 500);
});

// Mendefinisikan properti komponen
const props = defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    slider: Array,
    about: Array,
    skill: Array,
    posts: Array,

    laravelVersion: { type: String, required: true },
    phpVersion: { type: String, required: true },
    options: {
        theme: {
            controlsView: "standard",
            active: "light",
            light: {
                color: "#3D4852",
                backgroundColor: "#fff",
                opacity: "0.7",
            },
            dark: {
                color: "#fff",
                backgroundColor: "#202020",
                opacity: "0.7",
            },
        },
    },
});
const showingNavigationDropdown = ref(false);
</script>

<template>
    <Head title="Welcome" />
    <nav class="container py-4 bg-white border-gray-200">
        <div class="flex flex-wrap items-center justify-between">
            <span class="text-2xl font-extrabold text-purple-800">Taufik</span>
            <button
                @click="showingNavigationDropdown = !showingNavigationDropdown"
                id="toggleNavbar"
                type="button"
                class="inline-flex items-center p-2 ml-3 text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200"
            >
                <span class="sr-only">Open main menu</span>
                <svg
                    class="w-6 h-6"
                    aria-hidden="true"
                    fill="currentColor"
                    viewBox="0 0 20 20"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        fill-rule="evenodd"
                        d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
                        clip-rule="evenodd"
                    ></path>
                </svg>
            </button>
            <div
                :class="{
                    block: showingNavigationDropdown,
                    hidden: !showingNavigationDropdown,
                }"
                class="w-full sm:hidden md:block md:w-auto"
                id="navbarDefault"
            >
                <ul
                    class="flex flex-col items-center p-4 mt-4 font-medium border border-gray-100 rounded-lg md:p-0 bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:border-0 md:bg-white"
                >
                    <li>
                        <a
                            href="#"
                            class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-purple-500 md:hover:bg-transparent md:border-0 md:hover:text-purple-700 md:p-0"
                            >Home</a
                        >
                    </li>
                    <li>
                        <a
                            href="#"
                            class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-purple-500 md:hover:bg-transparent md:border-0 md:hover:text-purple-700 md:p-0"
                            >About</a
                        >
                    </li>

                    <li>
                        <a
                            href="#blogs"
                            class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-purple-500 md:hover:bg-transparent md:border-0 md:hover:text-purple-700 md:p-0"
                            >Blogs</a
                        >
                    </li>
                    <li>
                        <a
                            href="#"
                            class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-purple-500 md:hover:bg-transparent md:border-0 md:hover:text-purple-700 md:p-0"
                            >Contact</a
                        >
                    </li>
                    <li>
                        <div v-if="canLogin">
                            <Link
                                v-if="$page.props.auth.user"
                                :href="route('dashboard')"
                                class="px-4 py-2 mr-3 text-sm font-medium text-center text-white bg-purple-700 rounded-md hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300 md:mr-0"
                            >
                                Dashboard
                            </Link>
                            <template v-else>
                                <div class="flex gap-4">
                                    <Link
                                        :href="route('login')"
                                        type="button"
                                        class="px-4 py-2 mr-3 text-sm font-medium text-center text-white bg-purple-700 rounded-md hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300 md:mr-0"
                                    >
                                        Log in</Link
                                    >
                                    <Link
                                        :href="route('register')"
                                        type="button"
                                        class="px-4 py-2 mr-3 text-sm font-medium text-center text-black rounded-md bg-zinc-300 hover:bg-zinc-800 hover:text-white ocus:ring-4 focus:outline-none focus:ring-zinc-300 md:mr-0"
                                    >
                                        Register</Link
                                    >
                                </div>
                            </template>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container w-full h-screen">
        <div class="flex items-center justify-between">
            <div class="text-black lg:w-6/12">
                <div>
                    <h2 class="text-xl font-semibold text-purple-800">
                        Halo semua 👋, Saya
                    </h2>
                    <h1 class="my-2 text-4xl font-extrabold text-zinc-800">
                        Muhammad Taufik Hidayat
                    </h1>
                    <h3 class="text-xl text-zinc-700">
                        Mahasiswa & Web Developer
                    </h3>
                    <p class="my-4 text-base text-zinc-700">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Dolore non nobis molestiae alias qui accusamus laborum
                        error vitae nemo porro explicabo iste quam dolor, neque
                        nam assumenda. Eum blanditiis autem itaque quisquam
                        velit mollitia provident quae accusamus sequi natus ea
                        dolor magnam, laborum dicta saepe porro ad non culpa
                        perspiciatis!
                    </p>
                </div>
                <div class="grid grid-cols-1 gap-2 md:flex md:justify-start">
                    <button
                        type="button"
                        class="px-4 py-2 text-white bg-purple-800 rounded-lg hover:bg-purple-400 mt-7"
                    >
                        Get Started
                    </button>
                </div>
            </div>
            <div class="lg:w-6/12">
                <div class="w-full">
                    <LottieAnimation
                        :animation-data="WatermelonJSON"
                        :auto-play="true"
                        :height="100"
                        :loop="true"
                        :speed="1"
                        ref="anim"
                    />
                </div>
            </div>
        </div>
    </main>
    <section class="container" id="about">
        <h1 class="text-4xl font-extrabold text-center text-purple-800">
            About
        </h1>
        <div class="flex flex-col gap-4 my-10 text-base text-zinc-600">
            <div class="flex gap-12">
                <p class="w-1/2 text-justify">
                    Lorem ipsum dolor sit amet consectetur, adipisicing elit.
                    Voluptatem aliquid odit dolorum delectus veniam. Temporibus
                    sint eum illum expedita libero id nostrum, nam earum animi.
                    Vitae maxime delectus quisquam aut, tenetur obcaecati
                    commodi facere sit tempore quas consequuntur. Blanditiis
                    assumenda officiis maxime nesciunt sed in corrupti dolorum
                    vitae cupiditate mollitia.
                </p>
                <div class="w-1/2"></div>
            </div>
            <div class="flex gap-12">
                <div class="w-1/2"></div>
                <p class="w-1/2 text-justify">
                    Lorem ipsum dolor sit amet consectetur, adipisicing elit.
                    Veritatis illo voluptatum voluptatibus dolor nulla,
                    perspiciatis, commodi expedita quasi maxime provident
                    placeat? Aliquid fugit nobis quisquam est vero, maiores
                    pariatur temporibus, nesciunt rerum excepturi, sed deleniti
                    at soluta adipisci praesentium assumenda dicta repellat
                    minima quam repellendus dolore quis doloremque. Facere, est?
                </p>
            </div>
        </div>
    </section>
    <section class="container mt-32" id="blogs">
        <h1
            class="text-4xl font-extrabold text-center text-purple-800"
            v-if="posts"
        >
            Blogs
        </h1>
        <div class="flex flex-wrap gap-4 my-10 justify-evenly">
            <div
                v-for="post in posts"
                :key="post.id"
                class="max-w-sm overflow-hidden rounded shadow-lg"
            >
                <div class="px-6 py-4">
                    <div
                        class="mb-2 text-xl font-bold"
                        v-if="post && post.judul"
                    >
                        {{ post.judul }}
                    </div>
                    <p
                        class="text-base text-gray-700"
                        v-if="post && post.konten"
                    >
                        {{ post.konten }}
                    </p>
                    <p
                        class="text-sm text-zinc-400"
                        v-if="post && post.penulis"
                    >
                        Author: {{ post.penulis }}
                    </p>
                </div>
                <div class="px-6 pt-4 pb-2">
                    <span
                        v-if="post && post.kategori"
                        class="inline-block px-3 py-1 mb-2 mr-2 text-sm font-semibold text-gray-700 bg-purple-200 rounded-full"
                        >#{{ post.kategori }}</span
                    >
                </div>
            </div>
        </div>
    </section>
    <section class="container bg-white dark:bg-gray-900">
        <div class="max-w-screen-md px-4 py-8 mx-auto lg:py-16">
            <h2
                class="mb-4 text-4xl font-extrabold tracking-tight text-center text-purple-800 dark:text-white"
            >
                Contact Us
            </h2>

            <form action="#" class="space-y-8">
                <div>
                    <label
                        for="email"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                        >Your email</label
                    >
                    <input
                        type="email"
                        id="email"
                        class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-primary-500 focus:border-primary-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500 dark:shadow-sm-light"
                        placeholder="name@flowbite.com"
                        required
                    />
                </div>
                <div>
                    <label
                        for="subject"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                        >Subject</label
                    >
                    <input
                        type="text"
                        id="subject"
                        class="block w-full p-3 text-sm text-gray-900 border border-gray-300 rounded-lg shadow-sm bg-gray-50 focus:ring-primary-500 focus:border-primary-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500 dark:shadow-sm-light"
                        placeholder="Let us know how we can help you"
                        required
                    />
                </div>
                <div class="sm:col-span-2">
                    <label
                        for="message"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-400"
                        >Your message</label
                    >
                    <textarea
                        id="message"
                        rows="6"
                        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg shadow-sm border border-gray-300 focus:ring-primary-500 focus:border-primary-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500"
                        placeholder="Leave a comment..."
                    ></textarea>
                </div>
                <button class="p-2 text-white bg-purple-800 rounded-md">
                    Send message
                </button>
            </form>
        </div>
    </section>
    <footer class="bg-purple-800">
        <p class="py-8 text-xl font-thin text-center text-white">
            Muhammad Taufik Hidayat
        </p>
    </footer>
</template>
<style></style>
