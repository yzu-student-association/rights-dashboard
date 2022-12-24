<template>
    <div class="container p-px mx-auto h-full">
        <div :class="statusObj" class="border-t-8 w-4/5 bg-white mx-auto mt-4 border-gray-100 shadow p-5 rounded-md">
            <div class="flex justify-center">
                <img class="w-2/3" :src="imgStatus" alt="">
            </div>
            <h2 class="font-medium text-2xl">{{name}}</h2>
            <div v-if="description">
                <p>{{description}}</p>
            </div>
            <div v-else>
                <p>{{status}}</p>
            </div>
        </div>
    </div>
</template>

<script>
const statusColor = {
    "無法辦理": "border-t-red-500",
    "辦理完成": "border-t-green-500",
    "提案排程中": "border-t-gray-500",
    "辦理中": "border-t-blue-500",
    "研議中": "border-t-yellow-500",
    "提案中": "border-t-amber-500",
}

export default {
    name: 'card',
    props: ['name','status','description'],
    data: () => {
        return {

        }
    },
    computed: {
        statusObj() {
            return {
                [statusColor[this.status]]: true,
            }
        },
        imgStatus() {
            return `/imgs/${this.status}.png`
        }
    }
}
</script>
