<template>
    <div class="grid h-screen grid-cols-3 bg-slate-600">
        <aside class="col-span-1 bg-blue-600 text-blue-800">
            <ul class="space-y-3">
                <li :class="userSelecionado.name === user.name ? 'bg-purple-950 text-sky-300' : 'bg-purple-200'"
                    v-for="user in onlineUsers" @click="selectUser(user)">{{ user.name }}</li>

                <!-- <li @click="selectUser('Renata Marinho')">Renata Marinho</li>
                <li @click="selectUser('Nathala Franco')">Nathala Franco</li>
                <li @click="selectUser('Helenice Mota')">Helenice Mota</li> -->
            </ul>

        </aside>
        <main v-if="selectUser" class="flex flex-col justify-between col-span-2 bg-white">

            <div class="w-full p-2 flex flex-row space-x-2 items-center border border-b-purple-400">
                <UAvatar :src="userSelecionado.image" alt="Avatar" />
                <P class="font-semibold">{{ userSelecionado.name }}</P>
            </div>
            <div class="h-full flex flex-col item p-2 space-y-3 text-black">
                <div v-for="mensagem in mensagens" class="flex justify-end w-full">
                    <Mensagem :mensagem="mensagem" />
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

const onlineUsers = ref([
    {
        id: 1,
        image: 'https://i.pravatar.cc/100?img=7',
        name: "Leo Moura"
    },
    {
        id: 2,
        image: 'https://i.pravatar.cc/200?img=1',
        name: "Renata Marinho"
    },
    {
        id: 3,
        image: 'https://i.pravatar.cc/300?img=2',
        name: "Nathala Franco"
    },
    {
        id: 4,
        image: 'https://i.pravatar.cc/400?img=5',
        name: "Helenice Mota"
    }
])

const userSelecionado = ref(onlineUsers.value[0])

const selectUser = (user) => {
    userSelecionado.value = user
}

const sendMensage = () => {
    mensagens.value.push({ from: userSelecionado.value.name, content: mensagem.value })
    mensagem.value = ''
}

const sayHello = () => {
    alert("Olaaa")
}


</script>

<style scoped>
li {
    @apply border-solid border-purple-800 border-2 p-3 m-2 rounded-lg font-semibold cursor-pointer;
}

.self {
    @apply py-2 px-1 bg-blue-300 border-solid border-2 border-blue-800 w-fit rounded-lg;
}

.other {
    @apply py-2 px-1 bg-purple-200 border-solid border-2 border-purple-800 w-fit rounded-lg;
}
</style>