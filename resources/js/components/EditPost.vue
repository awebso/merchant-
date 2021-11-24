<template>
    <div>
        <h3 class="text-center">Edit Post</h3>
        <div class="row">
            <div class="col-md-6">
                <form @submit.prevent="updatePost">
                    <div class="form-group">
                        <label>Name</label>
                        <input type="text" class="form-control" v-model="post.name">
                    </div>
                    <div class="form-group">
                        <label>Trade Line</label>
                        <input type="text" class="form-control" v-model="post.trade_line">
                    </div>
                    <div class="form-group">
                        <label>Trade Type</label>
                        <input type="text" class="form-control" v-model="post.trade_type">
                    </div>
                    <button type="submit" class="btn btn-primary">Update Post</button>
                </form>
            </div>
        </div>
    </div>
</template>
  
<script>
    export default {
        data() {
            return {
                post: {}
            }
        },
        created() {
            this.axios
                .get(`http://127.0.0.1:8000/api/post/edit/${this.$route.params.id}`)
                .then((response) => {
                    this.post = response.data;
                    // console.log(response.data);
                });
        },
        methods: {
            updatePost() {
                this.axios
                    .post(`http://127.0.0.1:8000/api/post/update/${this.$route.params.id}`, this.post)
                    .then((response) => {
                        this.$router.push({name: 'home'});
                    });
            }
        }
    }
</script>