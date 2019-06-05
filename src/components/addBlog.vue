<template>
    <div id="add-blog">
        <h2>Add a New Blog Post</h2>
        <form v-if="!submitted">
            <label>Blog Title:</label>
            <input type="text" v-model.lazy="blog.title" required />
            <label>Blog Content:</label>
            <textarea v-model.lazy.trim="blog.content"></textarea>


        <div id="checkboxes">
        <label>Motivational</label>
        <input type="checkbox" value="Motivational" v-model="blog.categories" />
        <label>Romantic</label>
        <input type="checkbox" value="Romantic" v-model="blog.categories" />
        <label>Jokes</label>
        <input type="checkbox" value="Jokes" v-model="blog.categories" />
        <label>Informative</label>
        <input type="checkbox" value="Informative" v-model="blog.categories" />
        </div>
        <label>Author:</label>
        <select v-model="blog.author">
        <option v-for="author in authors">{{author}}</option>
        </select>

        <button v-on:click.prevent="post">Add post</button></form>
        <div v-if="submitted">
        <h3>Thanks for submitting</h3>
        </div>

        <div id="preview">
            <h3>Blog preview</h3>
            <p>Blog title: {{ blog.title }}</p>
            <p>Blog content:</p>
            <textarea rows="5" v-model.lazy= "blog.content"></textarea>
            <p><b>Blog categories:</b></p>
            <ul>
            <li v-for="category in blog.categories">{{category}}</li>

            </ul>
            <p><b>Author:</b>{{blog.author}}</p>


        </div>
            </div>
</template>

<script>
export default {
    data () {
        return {
            blog: {
                title: '',
                content: '',
                categories:[],
                author:""
            },
            authors:['Maxpayne','Immortal','Nirmohi'],
            submitted:false,
        }
    },
    methods: {
    post:function(){
    this.$http.post('https://blogspot623.firebaseio.com/posts.json',this.blog).then(function(data){
    console.log(data);
    this.submitted= true;
    });
    }

    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans:600');

#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
    font-family:'Open Sans',sans-serif;
}
#checkboxes input{
display:inline-block;
margin-right:10px;

}
#checkboxes label{
display:inline-block;
}
</style>
