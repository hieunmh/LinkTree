<template>
    <div>
        <ClientOnly>
            <input :id="placeholder" :placeholder="placeholder" :max-length="String(max)" 
                class="w-full bg-[#eff0eb] text-gray-800 border-2 text-sm border-[#eff0eb] 
                rounded-xl py-3.5 px-3 placeholder-gray-500 focus:outline-none"
                @focus="isFocused = true" @blur="isFocused = false"
                :class="isFocused ? 'border-gray-900': ''"
                :type="inputType" v-model="inputComputed" autocomplete="off"
            />
        </ClientOnly>

        <span v-if="error" class="text-red-500 text-[14px] font-semibold">
            {{ error }}
        </span>
    </div>
</template>

<script setup>

const emit = defineEmits(['update:input']);
const props = defineProps(['input', 'placeholder', 'max', 'inputType', 'error']);
const { input, placeholder, max, inputType, error } = toRefs(props);

let isFocused = ref(false);

const inputComputed = computed({
    get: () => input.value,
    set: (val) => emit('update:input', val)
});

</script>