<template>
    <h3> New Post</h3>
    <form @submit.prevent="submit">

        <input
            v-model="newPost.title"  
            placeholder="Title"
            type="text"
        />
        <br/>
        <textarea
            cols="50"
            rows="10"
            v-model="newPost.content"
        ></textarea>

        <button>Submit</button>

    </form>

</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { reactive } from 'vue';
import { usePosts } from '@/composable/usePosts';
import { useRouter } from 'vue-router';

export default defineComponent({
    name: "NewPost",
    setup(){

        const postStore = usePosts()

        const router = useRouter()

        console.log(router)
        
        const newPost = reactive({
            title: '',
            content: ''

        })

        const submit = () => {
            const idV = postStore.posts.value.length + 1
            postStore.addPost({
                id: idV,
                title: newPost.title,
                content: newPost.content,
                likes: 0,
                hashtags: []
            })

            router.push(`/posts/${idV}`)

        }

        return {
            newPost,
            submit
        }
    }
})
</script>