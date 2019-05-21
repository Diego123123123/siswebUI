<template>
    <div id="newspaper">
        <v-form v-on:submit.prevent="createNew">
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
        methods: {
            createNew(){
                this.$http.post(this.urlNewsPapers, {
                    title: this.title,
                    description: this.description,
                    author: this.author
                }).then(function(response) {
                    console.log(response)
                    this.$router.push({name: "home"})
                }).catch(function(error){
                    console.log(error)
                })
            }
        },
        data(){
            return { 
                urlNewsPapers : 'http://127.0.0.1:5000/newspapers',
                title : '',
                description: '',
                author: ''

            }
        }
    }
</script>

<style scoped>
#newspaper{
    height: 20%;
    width: 45%;
    text-align: center;
    margin-left: 25%;
}
</style>