<template>
    <div class="grid h-screen grid-cols-3 bg-slate-600">
        <aside class="col-span-1 bg-blue-600 text-blue-800">
            <ul class="space-y-3">
                <li @click="selectUser('Leo Moura')">Leo Moura</li>
                <li @click="selectUser('Renata Marinho')">Renata Marinho</li>
                <li @click="selectUser('Nathala Franco')">Nathala Franco</li>
                <li @click="selectUser('Helenice Mota')">Helenice Mota</li>
            </ul>

        </aside>
        <main v-if="selectUser" class="flex flex-col justify-between col-span-2 bg-white">
            <div class="space-y-3 p-2 text-blue-800">

                <div v-for="mensagem in mensagens" class="flex justify-end w-full">
                   <Mensagem :mensagem="mensagem"/>
                </div>
                
            </div>

            <div class="">
                <UInput v-model="mensagem" @keydown.enter="sendMensage" />
            </div>
        </main>
    </div>
</template>

<script setup>

const mensagem = ref('')
const mensagens = ref([])
const userSelecionado = ref(null);

const selectUser = (user) => {
    userSelecionado.value = user
}

const sendMensage = () => {
    mensagens.value.push({ from: userSelecionado.value, content: mensagem.value })
    mensagem.value = ''       
}

const sayHello = () => {
    alert("Olaaa")
}


</script>

<style scoped>
li {
    @apply bg-purple-200 p-3 m-2 rounded-lg font-semibold cursor-pointer;
}

.self {
    @apply  py-2 px-1 bg-blue-300 border-solid border-2 border-blue-800 w-fit rounded-lg;
}

.other {
    @apply py-2 px-1 bg-purple-200 border-solid border-2 border-purple-800 w-fit rounded-lg;
}

</style>