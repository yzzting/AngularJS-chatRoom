<script>
    export default {
        props:['userList','sessionIndex','session','search'],
        methods: {
            select (value) {
                this.sessionIndex = this.userList.indexOf(value);
            }
        },
        filters: {
            search (list) {
                return list.filter(item => item.name.indexOf(this.search) > -1)
            }
        }
    };
</script>

<template>
    <div class="m-list">
        <ul>
            <li v-for="item in userList | search" :class="{ active: session.userId === item.id }" @click="select(item)">
                <img class="avatar"  width="30" height="30" :alt="item.name" :src="item.img">
                <p class="name">{{item.name}}</p>
            </li>
        </ul>
    </div>
</template>

<style lang="less">
    .m-list {
        li {
            padding: 12px 15px;
            border-bottom:1px solid rgba(246, 74, 182, 0.66);
            cursor:pointer;
        }
        .avatar, .name {
            vertical-align: middle;
        }
        .avatar {
            border-radius: 2px;
        }
        .name {
            display: inline-block;
            margin: 0 0 0 15px;
        }
    }
</style>
