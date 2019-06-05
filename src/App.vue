<template>
    <div>
<app-header></app-header>
<router-view></router-view>
<app-footer></app-footer>
    </div>
</template>

<script>
import addBlog from './components/addBlog.vue';
import showBlogs from './components/showBlogs.vue';
import header from './components/header.vue';
import singleBlog from './components/singleBlog.vue';
import footer from './components/footer.vue';



export default {
    components: {
        'add-blog': addBlog,
        'show-blogs':showBlogs,
        'app-header':header,
        'single-blog':singleBlog,
        'app-footer':footer

    },
    data () {
        return {
        }
    },
    methods: {
    },

}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans:600');

body{
    margin: 0;
    // background:#EDE7F6;
   font-family: 'Open Sans',sans-serif;
}
</style>
