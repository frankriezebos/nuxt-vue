<template>
    <div class="container">
        <article 
            v-for="post in posts"
            :key="post.id"
            class="post--article-wrap"
        >
            <h1 class="post--article-title">{{ post.title }}</h1>
            <p class="post--article-content">{{ post.content.substring(0,100)+".." }}</p>
            
            <nuxt-link
                :to="{ name: 'posts-id', params: { id: post.id } }"
                :key="post.id"
                class="button--grey"
            >
                Read more
            </nuxt-link>
        </article>
    </div>
</template>

<script>
    export default {
        head() {
            return {
                title: 'All posts',
                meta: [{
                        hid: 'description',
                        name: 'description',
                        content: 'All posts'
                    },
                    {
                        name: 'twitter:title',
                        content: 'All posts'
                    },
                    {
                        name: 'twitter:description',
                        content: 'All posts'
                    },
                    {
                        name: 'twitter:image',
                        content: 'https://i.imgur.com/UYP2umJ.png'
                    },
                    {
                        name: 'twitter:card',
                        content: 'summary_large_image'
                    }
                ],
            };
        },
        computed: {
            posts() {
                return this.$store.state.posts.all;
            },
        },
    };
</script>

<style scoped>
    .container {
        text-align: left;
    }

    .post--article-wrap:first-of-type {
        margin-left: 10%;
    }

    .button--grey {
        margin-left: 0;
        margin-top: 20px;
    }
</style>