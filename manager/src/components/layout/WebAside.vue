<template>
    <div class="sidebar">
        <el-menu
            class="sidebar-el-menu"
            :default-active="onRoutes"
            :collapse="collapse"
            background-color="#3b9a9c"
            text-color="#F5F0F6"
            active-text-color="#fef4a9"
            unique-opened
            router
        >
            <template v-for="item in items">
                <template>
                    <el-menu-item :index="item.index" :key="item.index">
                        <i :class="item.icon"></i>
                        <span slot="title">{{ item.title }}</span>
                    </el-menu-item>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
import newPage from "../../utils/newPage";

export default {
    data() {
        return{
            collapse: false,
            items:[
                {
                    icon: 'el-icon-s-home',
                    index: 'info',
                    title: '系统首页'
                },
                {
                    icon: 'el-icon-microphone',
                    index: 'singer',
                    title: '歌手管理'
                },
                {
                    icon: 'el-icon-user-solid',
                    index: 'user',
                    title: '用户管理'
                },
                {
                    icon: 'el-icon-files',
                    index: 'songList',
                    title: '歌单管理'
                }
            ]
        }
    },
    computed:{
        onRoutes(){
            return this.$route.path.replace('/', '')
        }
    },
    created(){
        newPage.$on('collapse', msg => {
            this.collapse = msg
        })
    }
}
</script>

<style scoped>
.sidebar {
    display: block;
    position: absolute;
    background-color: #6b778d;
    left: 0;
    top: 70px;
    bottom: 0;
    overflow-y: scroll;
}
.sidebar::-webkit-scrollbar {
    width: 0;
}
.sidebar-el-menu:not(.el-menu--collapse) {
    width: 150px;
}
.sidebar > ul {
    height: 100%;
}
</style>