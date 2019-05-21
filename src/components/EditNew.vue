<template>
    <div id="newspaperedit">
        <v-form v-on:submit.prevent="editNew">
            <v-text-field
                    v-model="title"
                    label="Title"
                    required
            ></v-text-field>
            <v-text-field
                    v-model="description"
                    label="Description"
                    required>
            </v-text-field>
            <v-text-field
                    v-model="author"
                    label="Author"
                    required
            ></v-text-field>

            <v-btn
            type="submit"
            >submit</v-btn>
        </v-form>
    </div>
</template>

<script>
    export default {
        name: "PostNewsPaper",
        created: function(){
            console.log('-----------------')
            this.$http.get(this.urlNewsPapers + '/' +  this.$route.params['id']).then(function(response) {
                console.log(response)
                this.author = response.body.author;
                this.title = response.body.title;
                this.description = response.body.description
            }).catch(function(error){
            })
            console.log('-----------------')
        },
        methods: {
            printRoute() {
            },
            getUser(id) {
                this.$http.get(this.urlNewsPapers).then(function(response) {
                }).catch(function(error){
                })
            },
            editNew(){
                this.$http.put(this.urlNewsPapers + '/' + this.$route.params['id'], {
                    title: this.title,
                    description: this.description,
                    author: this.author
                }).then(function(response) {
                    this.$router.push({name: "home"})
                }).catch(function(error){
                })
            }
        },
        data(){
            return { 
                urlNewsPapers : 'http://127.0.0.1:5000/newspapers',
                title : '',
                description: '',
                author: '',
            }
        }
    }
</script>

<style scoped>
#newspaperedit{
    height: 20%;
    width: 45%;
    text-align: center;
    margin-left: 25%;
}
</style>