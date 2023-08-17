<template>
    <AdminLayout>
        <div id="AdminPage" class="flex h-[100vh] pb-4">
            <div class="lg:w-[calc(100% - 500px)] md:w-[calc(100%-330px)] w-full md:pt-20 pt-14">
                <div class="max-w-[750px] mx-auto pb-24">
                    <button v-if="userStore.isMobile || !showAddLink" @click="showAddLinkFunc()"
                        class="flex items-center justify-center w-full py-3 rounded-full 
                            text-white font-semibold bg-[#8228d9] hover:bg-[#6c21b3]"
                        :class="userStore.isMobile ? 'mt-8 text-xl' : 'mt-20 md:mt-8'"
                    >
                        <Icon name="mdi:plus" v-if="!userStore.isMobile" class="mr-0.5" size="25" />

                        <span v-if="!userStore.isMobile">Add link</span>

                        <span v-if="userStore.isMobile">Add new link</span>
                    </button>

                    <AddLink 
                        v-if="!userStore.isMobile" @close="showAddLink = false"
                        :class="[
                            {'mt-20 md:mt-8 mb-12 max-h-[1000px] transition-all duration-300 ease-in': showAddLink},
                            {'max-h-0 transition-all duration-300 ease-out' : !showAddLink}
                        ]"
                    />

                    <div v-for="link in fakeLink" class="mt-4">
                        <LinkBox v-if="link" :link="link" 
                            :selectedId="selectedInput.id"
                            :selectedStr="selectedInput.str"
                            @updatedInput="updatedInput"
                            class="mt-6"
                        />
                    </div>
                </div>
            </div>

            <MobileSectionDisplay />
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

let selectedInput = ref({ id: 0, str: '' });

let showAddLink = ref(false);

let updatedInput = (e) => {
    selectedInput.value.id = e.id;
    selectedInput.value.str = e.str;
}

let showAddLinkFunc = () => {
    if (userStore.isMobile) {
        userStore.addLinkOverlay = true;
    } else {
        showAddLink.value = true;
    }
}

</script>