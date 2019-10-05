<template>
    <div>
        <Form v-on:update-table="UPDATE_TABLE_DATA"/>

        <b-container>
            <b-table  striped hover :items="articles"></b-table>
        </b-container>
    </div>
</template>

<script>
import axios from 'axios';
import Form from './Form.vue'

export default {
    name: "Table",
    data() {
        return {

            articles: [],
        }
    },
    components: {
        Form,
    },
    methods: {

        async FETCH_TABLE_DATA() {

            try {
                
                const response = await axios.get('http://laravel.devel/api/articles');

                this.articles = response.data;
            } 
            catch (error) {
                // eslint-disable-next-line
                console.log(error);
            }
        },

        UPDATE_TABLE_DATA(payload) {
            
            this.articles.unshift(payload);
        }
    },
    created () {

        this.FETCH_TABLE_DATA();
    },

}
</script>

<style>

</style>