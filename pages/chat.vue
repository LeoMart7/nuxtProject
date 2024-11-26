<template>
    <div class="grid grid-cols-3 h-screen">
        <aside class="border-blue-900 border col-span-1 bg-blue-600 text-blue-800">

            <ul>
                <li @click="selectUser('Leo Moura')">Leo Moura</li>
                <li @click="selectUser('Renata Marinho')">Renata Marinho</li>
                <li @click="selectUser('Nathala Franco')">Nathala Franco</li>
                <li @click="selectUser('Helenice Mota')">Helenice Mota</li>
            </ul>

        </aside>
        <main class="bg-purple-200 col-span-2 flex flex-col justify-between">
            <div class="space-y-2 p-2 text-blue-800">
                
               <div @click="selectUser" class="w-full flex justify-end">
                    <div class="self" >
                        {{ userSelecionado }}
                    </div>
               </div>

                <div v-for="message in mensagens" class="w-full flex justify-end">
                    <div class="self">
                        <p>{{ message.content }}</p>
                    </div>
                </div>

                <div class="w-full flex justify-start">
                    <div class="other">
                        <p>mensagem 2</p>
                    </div>
                </div>

                

            </div>

            <div class=" bg-blue-600">
                <UInput v-model="value"/>
                
            </div>

        </main>
    </div>
</template>

<script setup>

const userSelecionado = ref(null);

const selectUser = (user) => {
    userSelecionado.value = user;
}


const sayHello = () => {
    alert("Hello wolrd!!")
}

const mensagens = ref([
    {
        content:'Olá!'
    },
    {
        content:'Oi!'
    }
])

</script>

<style scoped>
li {
    @apply bg-purple-200 p-3 m-2 rounded-lg font-semibold cursor-pointer;
}

.self {
    @apply w-fit py-2 px-1 bg-blue-300 border-blue-800 border rounded-lg;
}

.other {
    @apply w-fit py-2 px-1 bg-blue-200 border-blue-800 border rounded-lg;
}
</style>