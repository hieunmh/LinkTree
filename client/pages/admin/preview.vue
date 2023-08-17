<template>
    <div class="fixed overflow-auto w-full h-screen" :class="userStore.theme" />

    <AdminLayout>
        <div id="PreviewAdminPage" class="w-full mx-auto pt-32 relative z-10">
            <div class="mx-auto w-full">
                <div class="h-full mx-auto w-full">
                    <img class="rounded-full min-w-[120px] w-[120px] mx-auto" src="https://picsum.photos/id/8/300/320" />

                    <div class="text-center text-2xl font-semibold mt-2"
                        :class="userStore.theme"   
                    >
                        Minh Hieu
                    </div>

                    <div class="text-center text-lg font-normal mt-2 mb-10"
                        :class="userStore.theme"
                    >
                        <div class="px-8">
                            This is bio section !!!
                        </div>
                    </div>

                    <div v-for="link in fakeLink">
                        <a :href="link.url" target="_blank"
                            class="flex items-center relative w-[calc(100%-10px)] mx-auto border bg-white mt-4 p-1 rounded-lg"
                        >
                            <img class="rounded-full h-[55px] aspect-square" :src="link.image" />

                            <div class="absolute text-[20px] font-medium text-center w-full">
                                {{ link.name }}
                            </div>
                        </a>
                    </div>

                    <div class="pb-12" />
                </div>
            </div>
        </div>
    </AdminLayout>
</template>

<script setup>
import AdminLayout from '~/layouts/AdminLayout.vue';

import { useUserStore } from '~/stores/user';
const userStore = useUserStore();

definePageMeta({ middleware: 'is-logged-out' });

const fakeLink = [
    {
        id: 1,
        name: 'Phuong Anh',
        url: 'https://www.facebook.com/ctpanh.uet',
        image: 'https://scontent.fsgn2-4.fna.fbcdn.net/v/t39.30808-6/351921715_789018182729073_2175936877863928048_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=09cbfe&_nc_ohc=__JAuTXfh_IAX99_ioi&_nc_ht=scontent.fsgn2-4.fna&oh=00_AfCv3LGz3PaLaT2gFiePCTbaSZrrKT5sKg8gR1_QzNdUeg&oe=64E12808'
    },

    {
        id: 2,
        name: 'Minh Hieu',
        url: 'https://www.facebook.com/pt.hieunm',
        image: 'https://scontent.fsgn2-7.fna.fbcdn.net/v/t39.30808-6/344386661_1743377549451566_5888987477625155345_n.jpg?_nc_cat=100&ccb=1-7&_nc_sid=09cbfe&_nc_ohc=nzjBF4l6cbYAX8WSPcK&_nc_ht=scontent.fsgn2-7.fna&oh=00_AfAo2DJ6faIzPUkboIBSv3QmYveQF84QUzvGJH6_fGKezQ&oe=64E1D401'
    },

];

</script>