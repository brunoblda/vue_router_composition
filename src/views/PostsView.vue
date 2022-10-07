
<template>
    <h4>Hello Posts</h4>
    <router-link to="/posts/new">New Post</router-link>
    <ul>
        <li 
            v-for="post in posts"
            :key="post.id"
        >
            <router-link
                :to="`/posts/${post.id}`"
            >
                {{post.title}}
            </router-link>
        </li>
    </ul>
    <router-view></router-view>
</template>

<script lang="ts">
import { usePosts } from '@/composable/usePosts'

import { defineComponent } from 'vue'
import {testPosts } from '@/composable/testPosts'

export default defineComponent({
    name: "PostsView",
    setup(){

        const postStore = usePosts()
        return{
            posts: postStore.posts
        }
    }
        
    
})
</script>