<template>
    <NotificationHeader @onReadAll="readAll" :unreadCount="unreadCount"/>
    <main>
        <NotificationItem
            v-for="notification in notifications"
            v-bind:key="notification.id"
            :notification="notification"
            :notificationRead="notification.read"
            @onReadNotification="notificationRead"
        />
    </main>
</template>

<script>
import NotificationHeader from './components/NotificationHeader.vue';
import NotificationItem from './components/NotificationItem.vue';
import notificationsData from './data/notifications.json'
export default {
    name: 'App',
    components: {
        NotificationHeader,
        NotificationItem
    },
    data(){
        return {
            notifications: [],
            notificationsCount: null,
            unreadCount: null,
        }
    },
    methods: {
        countUnreadNotification(){
            this.unreadCount = this.notifications.filter(item => {
                if (!item.read)
                    return true
                return false
            }).length
        },
        notificationRead(id){
            this.notifications.filter(item => {
                if (item.id==id) {
                    item.read = !item.read
                }
            })
            this.countUnreadNotification()
        },
        readAll(){
            this.notifications.forEach(notification => {
                notification.read = true
            })
            this.countUnreadNotification()
        },
    },
    created(){
        this.notifications = notificationsData
        this.notificationsCount = this.notifications.length
        this.countUnreadNotification()
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@500;800&display=swap');
body {
    font-family: 'Plus Jakarta Sans', sans-serif;
    @apply
        m-0
        flex
        lg:items-center
}
html,body {
    @apply
        h-full
        bg-Very-light-grayish-blue
}
#app {
    @apply
        mx-auto
        h-auto
        bg-white
        shadow-xl
        shadow-light-grayish-blue-1
        lg:w-[593px]
        lg:rounded-xl
        lg:px-2
}
main {
    @apply
        px-4
        bg-white
}
</style>
