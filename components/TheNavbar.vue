<template>
    <nav class="navbar">
        <div class="navbar--logowrap">
            <nuxt-link :to="{name: 'index'}" class="navbar--logowrap-logo">
                <img src="https://i.imgur.com/UYP2umJ.png" alt="Vue">
            </nuxt-link>

            <span class="navbar--logowrap-subheader">
                A Vue School course
            </span>
        </div>

        <div class="navbar--nav">
            <nuxt-link :to="{name: 'all-posts'}" class="navbar--nav-link">
                All Posts
            </nuxt-link>

            <nuxt-link
            v-for="post in posts"
            :to="{ name: 'posts-id', params: { id: post.id } }"
            :key="post.id"
            class="navbar--nav-link"
            >
                {{post.title}}
            </nuxt-link>
        </div>
    </nav>
</template>

<script>
export default {
    computed: {
        posts() {
            return this.$store.state.posts.all;
        },
    }
}
</script>

<style scoped>
    
</style>