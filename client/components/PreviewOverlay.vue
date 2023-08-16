<template>
    <div id="PreviewOverlay" class="md:hidde fixed bg-white z-30 top-0 left-0 h-full w-full overflow-auto"
        :class="userStore.theme"
    >
        <div id="PreviewOverlayToNav" class="w-full fixed z-10 items-center justify-between">
            <div class="flex items-center justify-between px-2 py-[8px] pl-4 bg-white w-full border-b">
                <div class="flex items-center justify-start w-full">
                    <button @click="userStore.isPreviewOverlay = false">
                        <img class="w-[23px] min-w-[23px] select-none" 
                            src="~/assets/image/linktree-logo-icon.png"
                        />
                    </button>
                </div>

                <div class="flex items-center justify-between gap-3">
                    <button class="flex items-center text-sm font-semibold p-2 rounded-full hover:bg-gray-200">
                        <Icon name="healthicons:megaphone-outline" class="mr-0.5" size="22" />
                    </button>

                    <button class="flex items-center font-semibold px-3 py-2 rounded-full hover:bg-gray-200">
                        <Icon name="mdi:lightning-bolt" class="mr-0.5" size="18" /> Upgrade
                    </button>

                    <button class="flex items-center font-semibold px-3 py-2 rounded-full border hover:bg-gray-200">
                        <Icon name="teenyicons:upload-solid" class="mr-1.5" size="18" /> Share
                    </button>
                </div>
            </div>
        </div>

        <div id="PreviewOverlayContentSection" class="relative w-full h-full mx-auto pt-24">
            <div class="mx-auto mb-16 w-full p-3">
                <div class="h-full mx-auto w-full overflow-auto z-10">
                    <img class="rounded-full min-w-[100px] w-[100px] mx-auto" 
                        src="https://picsum.photos/id/8/300/320"
                    />

                    <div class="text-center text-xl font-semibold mt-4"
                        :class="userStore.theme"
                    >
                        Minh Hieu
                    </div>

                    <div class="text-center font-light mt-2"
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
                            <img class="rounded-full h-[45px] aspect-square" :src="link.image" />

                            <div class="absolute text-[16px] text-center w-full">
                                {{ link.name }}
                            </div>
                        </a>
                    </div>

                    <div class="pb-28" />
                </div>
            </div>
        </div>

        <div id="PreviewButton" class="fixed bottom-10 w-full flex items-center justify-center">
            <button @click="userStore.isPreviewOverlay = false" 
                class="flex items-center justify-center p-2.5 bg-[#dfe2d9] rounded-full"
            >   
                <Icon name="mdi:close" size="30" />
            </button>
        </div>
    </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user';
const userStore = useUserStore();

onUnmounted(() => userStore.isPreviewOverlay = false);

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