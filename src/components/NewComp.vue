<template>
    <div>
        <div v-for="(user,index) in users" :key="index">
        <slot :user="user">{{ user.name }}</slot>
    </div>
    </div>
</template>

<script>
export default {
    props : ['users']
}
</script>

<style>

</style>
