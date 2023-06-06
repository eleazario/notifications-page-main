<template>
    <header>
        <h3>Notifications</h3>
        <span class="unreadCount">{{ unreadCount }}</span>
        <div class="flex flex-auto justify-end">
            <button @click="readAll" class="buttonReadAll">Mark all as read</button>
        </div>
    </header>
</template>

<script>
export default {
    props: ['unreadCount'],
    methods: {
        readAll(){
            this.$emit('onReadAll')
        }
    }
}
</script>

<style scoped>
header {
    @apply  
        flex
        py-6
        px-4
}

h3 {
    @apply
        font-extrabold
        text-xl
        mr-2
}

.unreadCount {
    @apply
        bg-blue
        px-3
        rounded-md
        text-white
        font-extrabold
        self-center
}

.buttonReadAll {
    @apply
        text-sm
        text-dark-grayish-blue
}
.buttonReadAll:hover {
    @apply
        text-blue
}
</style>