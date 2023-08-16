<template>
    <div class="md:block fixed hidden right-0 lg:w-[500px] w-[310px] h-[calc(100%-20px)] 
        mt-[20px] mx-auto border-l border-l-gray-300 pt-20"
    >
        <div class="mx-auto mt-16 mb-16 flex items-center justify-center w-full 
            lg:max-w-[230px] max-w-[200px] lg:h-[460px] h-[400px] p-3 rounded-3xl relative"
        >
            <img class="absolute z-10 pointer-events-none select-none" 
                src="~/assets/image/mobile-case.png"
            />

            <div class="w-full h-full absolute lg:max-w-[220px] max-w-[195px] rounded-3xl z-0"
                :class="userStore.theme"
            />

            <div class="h-full mx-auto w-full overflow-auto z-10">
                <img class="rounded-full min-w-[60px] w-[60px] mx-auto mt-8" src="https://picsum.photos/id/8/300/320" />

                <div class="text-center text-sm font-semibold mt-4 break-words"
                    :class="userStore.theme"   
                >
                    Minh Hieu
                </div>

                <div class="text-center text-[8px] font-semibold mt-2"
                    :class="userStore.theme"
                >
                    <div class="px-8 break-words">
                        This is bio section !!!
                    </div>
                </div>

                <div v-for="link in fakeLink">
                    <a :href="link.url" target="_blank"
                        class="flex items-center relative w-[calc(100%-10px)] mx-auto border bg-white mt-2 p-1 rounded-xl"
                    >
                        <img class="rounded-full h-[30px] aspect-square" :src="link.image" />

                        <div class="absolute w-full">
                            <div class="max-w-[70%] w-full mx-auto text-[10px] text-center font-semibold">
                                {{ link.name }}
                            </div>
                        </div>
                    </a>
                </div>

                <div class="pb-12" />
            </div>
        </div>
    </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user';
const userStore = useUserStore();

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