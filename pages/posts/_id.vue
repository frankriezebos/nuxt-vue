<template>
    <div class="container">
        <div class="post--article-back">
            <nuxt-link 
            :to="{name: 'all-posts'}" 
            class="button--grey">
                Back to all posts
            </nuxt-link>
        </div>
        
        <article class="post--article-wrap">
            <h1 class="post--article-title">{{ post.title }}</h1>
            <p class="post--article-content">{{ post.content }}</p>
        </article>

        <aside class="post--article-sidebar">
            <h3>Related posts</h3>
            <ul>
                <li v-for="related in relatedPosts" :key="related.id">
                    <nuxt-link :to="{ name: 'posts-id', params: { id: related.id } }">
                        {{ related.title }}
                    </nuxt-link>
                </li>
            </ul>
        </aside>
    </div>
</template>

<script>
    export default {
        head() {
            return {
                title: this.post.title,
                meta: [{
                        hid: 'description',
                        name: 'description',
                        content: this.post.content
                    },
                    {
                        name: 'twitter:title',
                        content: this.post.title
                    },
                    {
                        name: 'twitter:description',
                        content: this.post.content
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
        data() {
            return {
                id: this.$route.params.id,
            };
        },
        computed: {
            post() {
                return this.$store.state.posts.all.find((post) => post.id === this.id);
            },
            relatedPosts() {
                return this.$store.state.posts.all.filter((post) => post.id !== this.id);
            },
        },
    };
</script>

<style scoped>
    .container {
        text-align: left;
        display: block;
        max-width: 1000px;
        margin: 0 auto;
    }

    .button--grey {
        margin-left: 0;
    }

    .post--article-wrap,
    .post--article-sidebar {
        float: left;
    }

    .post--article-back {
        margin: 100px 0;
    }
</style>