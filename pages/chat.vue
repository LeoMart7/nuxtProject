<template>
    <div class="grid grid-cols-3 h-screen">
        <aside class="border-blue-900 border col-span-1 bg-blue-600 text-blue-800">

            <ul>
                <li @click="sayHello">Leo Moura</li>
                <li>Renata Marinho</li>
                <li>Nathala Franco</li>
                <li>Helenice Mota</li>
            </ul>

        </aside>
        <main class="bg-purple-200 col-span-2 flex flex-col justify-between">
            <div class="space-y-2 p-2 text-blue-800">
                
                {{ mensagem }}

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

                <div class="w-full flex justify-end">
                    <div class="self">
                    <p>mensagem 3</p>
                    </div>
                </div>

                <div class="w-full flex justify-start">
                    <div class="other">
                        <p>mensagem 4</p>
                    </div>
                </div>

            </div>

            <div class=" bg-blue-600">
                <input v-model="mensagem" class="rounded-lg border-gray-500 border w-full p-2 m-1" type="text">
            </div>

        </main>
    </div>
</template>

<script setup>

const sayHello = () => {
    alert("Hello wolrd!!")
}

const mensagem = ref('') 

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