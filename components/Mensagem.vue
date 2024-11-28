<template>
    <div class="self">
        <p class="font-semibold text-purple-800">{{ mensagem.from }}</p>
        <p>{{ mensagem.content }}</p>
    </div>
</template>

<script setup>
const props = defineProps({
    mensagem: {
        type: Object,
        required: true
    }
})

</script>