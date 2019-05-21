<template>
  <div id="home">
    <v-toolbar
            color="pink"
            dark
    >
      <v-toolbar-title>ALL NEWS</v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>

    <v-card>
      <v-container
              fluid
              grid-list-lg
      >
        <ul>
          <li v-for="elem in listOfNewspapers">
            <div class="mycard" v-bind:id="elem.id">
              <v-layout row wrap>
                  <v-flex xs12>
                    <v-card color="blue-grey darken-2" class="white--text">
                      <v-card-title primary-title>
                        <div>
                          <div class="headline">TITLE : {{elem.title}}</div>
                          <span>AUTHOR : {{elem.author}}</span>
                        </div>
                      </v-card-title>
                      <v-card-actions>
                        <v-btn flat dark>DESCRIPTION : {{elem.description}}</v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-flex>
                </v-layout>
                <v-btn
                color="error"
                @click="deleteNew(elem.id)"
                >
                  REMOVE
                </v-btn>
                <router-link v-bind:to="'change-news/' + elem.id">EDIT</router-link>
            </div>
          </li>
        </ul>
      </v-container>
    </v-card>
  </div>
</template>
<style>

</style>

<script>

  export default {
    data(){
      return {
          urlNewsPapers : 'http://127.0.0.1:5000/newspapers',
          listOfNewspapers : []
      }
    },
    components: {

    },
    created(){
        this.getAllNewsPapers()
    },
    methods: {
        getAllNewsPapers() {
            this.$http.get(this.urlNewsPapers).then(function (response) {
                this.listOfNewspapers = response.body;
            })
        },
        deleteNew(id) {
          this.$http.delete(this.urlNewsPapers + '/' + id).then(function(response) {
            this.$router.push({name: "home"});
            // $('#' + id).hide();
             window.location.reload();
          }).catch(function(error){
            console.log(error);
          })
        }
    }
  }
</script>
<style>
  li{
    width: 30%;
    display: inline-block;
  }

  .mycard{
    background-color: #92B0B3;
    margin-left: 15px;
    margin-right: 15px;
    margin-top: 20px;
  }
</style>
