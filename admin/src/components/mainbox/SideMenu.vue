<template>
    <!-- 动态创建菜单 -->
    <el-aside width="auto">
        <el-menu class="el-menu-vertical-demo"
         :default-active="route.path"
         active-text-color="#ffd04b"         
         :collapse="$store.state.isCollapse"
         router>
            <el-menu-item index="/index">
                <template #title>
                    <el-icon>
                        <HomeFilled />
                    </el-icon>
                    <span>首页</span>
                </template>
            </el-menu-item>
            

            <el-menu-item index="/center">
                <el-icon><Avatar /></el-icon>
                <span>个人中心</span>
            </el-menu-item>

            <el-sub-menu index="/user-manage" v-admin>
                <template #title>
                    <el-icon><UserFilled /></el-icon>
                    <span>用户管理</span>
                </template>
                <el-menu-item index="/user-manage/adduser">添加用户</el-menu-item>
                <el-menu-item index="/user-manage/userlist">用户列表</el-menu-item>
            </el-sub-menu>

            <el-sub-menu index="/news-manage">
                <template #title>
                    <el-icon><MessageBox /></el-icon>
                    <span>新闻管理</span>
                </template>
                <el-menu-item index="/news-manage/addnews">添加新闻</el-menu-item>
                <el-menu-item index="/news-manage/newslist">新闻列表</el-menu-item>
            </el-sub-menu>

            <el-sub-menu index="/product-manage">
                <template #title>
                    <el-icon><Reading /></el-icon>
                    <span>产品管理</span>
                </template>
                <el-menu-item index="/product-manage/addproduct">添加产品</el-menu-item>
                <el-menu-item index="/product-manage/productlist">产品列表</el-menu-item>
            </el-sub-menu>
            
        </el-menu>
    </el-aside>
</template>
    
<script setup>
import { ref } from 'vue'
import {
    HomeFilled,
    Avatar,UserFilled,MessageBox,Reading
} from '@element-plus/icons-vue'
import {useRoute} from 'vue-router'
import store from '@/store';
const route = useRoute()
const vAdmin ={
    mounted(el) {
        if(store.state.userInfo.role !==1){
            el.parentNode.removeChild(el)
        }
    },
}
</script>
    
<style scoped lang="scss">
.el-aside {
    height: 100vh;
    .el-menu{
        height: 100vh;
    }
}
</style>