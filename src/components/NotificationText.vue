<template>
    <div class="text-dark-grayish-blue text-[0.825rem]">
        <a href="" class="text-very-dark-blue mr-1">{{ notification.person }}</a>
        <span v-if="notification.type=='postReact'">
            <span class="mr-1">reacted to your recent post</span>
            <a href="">{{ notification.post }}</a>
        </span>
        <span v-if="notification.type=='follow'">
            followed you
        </span>
        <span v-if="notification.type=='join'">
            <span class="mr-1">has joined your group</span>
            <a href="" class="font-">{{ notification.group }}</a>
        </span>
        <span v-if="notification.type=='left'">
            <span class="mr-1">has left the group</span>
            <a href="" class="font-">{{ notification.group }}</a>
        </span>
        <span v-if="notification.type=='message'">
            sent your a private message
        </span>
        <span v-if="notification.type=='pictureComment'">
            commented on your picture
        </span>
        <slot></slot>
    </div>
</template>
<script>
export default {
    props: ['notification']
}
</script>
<style>
a {
    @apply
        font-extrabold
}

a:hover {
    @apply
        text-blue
}
</style>