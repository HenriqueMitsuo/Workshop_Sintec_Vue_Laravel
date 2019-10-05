<template>
  <b-container class="mt-3">
      <b-form @submit="CreateArticle">
        <!-- CAIXA DE TEXTO: TITULO -->
        <b-form-group id="input-group-1" label="Titulo:" label-for="input-1">
            <b-form-input
                id="input-1"
                v-model="title"
                type="title"
                required
                placeholder="Digite o titulo...">
            </b-form-input>
        </b-form-group>

        <!-- CAIXA DE TEXTO: CORPO DO TEXTO -->
        <b-form-group id="input-group-2" label="Texto:" label-for="input-2" description="">
            <b-form-textarea
                id="input-2"
                v-model="body"
                placeholder="Enter something..."
                rows="3"
                max-rows="6">
            </b-form-textarea>
        </b-form-group>

        <!-- BOTÃO -->
        <b-form-group>
            <b-button block variant="primary" type="submit">Enviar</b-button>
        </b-form-group>
  </b-form>
  </b-container>
</template>

<script>
import axios from 'axios';

export default {
    name: "Form",
    data() {
        return {
            title: '',
            body: '',
        }
    },
    methods: {
        async CreateArticle(event) {
            try {
                
                event.preventDefault();

                const request = await axios.post('http://laravel.devel/api/article', {
                    title: this.title,
                    body: this.body
                });

                this.title = '';
                this.body = '';
                
                this.$emit('update-table', request.data); 
            } 
            catch (error) {
                // eslint-disable-next-line
                console.log(error);
            }
        }
    },
}
</script>

<style>

</style>