
<template>
    <h4> {{post.title}}</h4> 
    <p>
        {{post.content}}
    </p>
</template>

<script lang="ts">
import { computed } from '@vue/reactivity';
import { defineComponent } from 'vue'
import { useRoute } from 'vue-router';
import { usePosts } from '@/composable/usePosts';

export default defineComponent({
    name: "PostView",
    setup(){
        const route = useRoute()
        const postStore = usePosts()

        const post: any = computed(() => 
        postStore.posts.value.find(x  => x.id.toString() === 
        route.params.id))
        console.log(route)

        return{
            post
        }
    }

    
        

})
</script>
