<template>
    <button @click.prevent="readNotification" :class="['notificationItem', {'notificationUnread': !notificationRead}]">
        <img :src="require(`@/images/${notification.avatar}`)" class="cursor-pointer mr-3 mt-1 object-contain w-10 self-start">
        <div class="mr-3">
            <div class="flex">
                <NotificationText :notification="notification">
                    <span v-if="!notificationRead" class="redDot"></span>
                </NotificationText>
            </div>
            <div class="text-grayish-blue">{{ notification.time }}</div>
            <div v-if="notification.type=='message'" class="messageBox">
                {{ notification.message }}
            </div>
        </div>
        <a href="" v-if="notification.type=='pictureComment'" class="pictureLink">
            <img :src="require(`@/images/${notification.picture}`)">
        </a>
    </button>
</template>
<script>
import NotificationText from './NotificationText.vue'
export default {
    props: ["notification", 'notificationRead'],
    components: { NotificationText },
    methods: {
        readNotification(){
            this.$emit('onReadNotification', this.notification.id)
        }
    }
}
</script>
<style>
.notificationItem {
    @apply
        flex
        w-full
        text-start
        p-3
        pr-0
        mb-2
        text-sm
}
.notificationUnread {
    @apply
        bg-Very-light-grayish-blue
}
.redDot {
    @apply
        bg-red
        ml-1
        px-1
        h-2
        inline-block
        rounded-full
}
.pictureLink {
    @apply
        ml-auto
        mr-3
}

.pictureLink > img {
    @apply
        m-0 
        mt-1 
        w-10 
        self-start
}

.pictureLink > img:hover {
    @apply
        outline
        outline-4
        outline-light-grayish-blue-2
        rounded-md
}

.messageBox {
    @apply
        mt-3 
        p-3
        border
        border-light-grayish-blue-2
        text-dark-grayish-blue
        rounded-md
        cursor-pointer
}

.messageBox:hover {
    @apply
        bg-light-grayish-blue-2
}
</style>