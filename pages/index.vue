<template>
    <div class="container">
        <div class="content">
            <Logo />

            <h1 class="content--title">Hi there</h1>

            <div class="content--links">
                <nuxt-link 
                :to="{name: 'all-posts'}" 
                class="button--grey">
                    All Posts
                </nuxt-link>

                <nuxt-link
                v-for="post in posts"
                :to="{ name: 'posts-id', params: { id: post.id } }"
                :key="post.id"
                class="button--grey"
                >
                    {{ post.title }}
                </nuxt-link>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    head() {
        return {
            title: "Homepage",
            meta: [
                {
                    hid: "description",
                    name: "description",
                    content: "Nuxt Fundamentals by Vue School",
                },
                {
                    name: "twitter:title",
                    content: "Homepage",
                },
                {
                    name: "twitter:description",
                    content: "Nuxt Fundamentals by Vue School",
                },
                {
                    name: "twitter:image",
                    content: "https://i.imgur.com/UYP2umJ.png",
                },
                {
                    name: "twitter:card",
                    content: "summary_large_image",
                },
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

<style>
.container {
    margin: 0 auto;
    min-height: 70vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.content--title {
    font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
}

.content--subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
}

.content--links {
    padding-top: 15px;
}
</style>
