<template>
    <div>
        <h3 class="text-center">Add Post</h3>
        <div class="row">
            <div class="col-md-6">
                <form @submit.prevent="addPost">
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
                    <button type="submit" class="btn btn-primary">Add Post</button>
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
        methods: {
            addPost() {
  
                this.axios
                    .post('http://127.0.0.1:8000/api/post/add', this.post)
                    .then(response => (
                        this.$router.push({name: 'home'})
                        // console.log(response.data)
                    ))
                    .catch(error => console.log(error))
                    .finally(() => this.loading = false)
            }
        }
    }
</script>