<template>
    <div>
        <input v-model="user" placeholder="Introduce nombre de usuario de Github" v-show="input" v-on:keydown="obtenerUsuario">
        <div class="alert alert-warning" role="alert" v-show="advertencia">El usuario no existe</div>
        <div class="card" style="width: 18rem;" v-show="input">
            <img src="userData.avatar_url" alt="#" class="card-img-top">
            <div class="card-body">
                <h3 class="card-title" href="userData.login">Titulo</h3>
                <p class="card-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatem quae velit totam doloribus atque molestiae animi tempore odio natus mollitia explicabo dolorem accusamus ut voluptas,</p>
                <a href="#" class="btn btn-primary" v-on:keydown="obtenerUsuario">Pincha</a>
                <a href="userData.html_url" class="card-link">URL de Github</a>
            </div>
        </div>
        <!-- TODO: Crear componente GitHub -->
    </div>
</template>

<script>

// TODO: Importar componente GitHubRepos
import GitHubRepos from './GitHubRepos.vue'

export default {
    name: 'GitHub',
    components: {
        GitHubRepos
        // TODO: Importar componente GitHubRepos
    },
    data: function() {
        return {
            user: 'vuejs',
            input: true,
            advertencia: false,
            card: false,
            userData: "",
            repolist: "" 

            // TODO: crear variables de datos para el funcionamiento del componente
        }
    },
    methods: {
        obtenerUsuario: function() {
            // TODO: Función para obtener los datos de usuario de la API de GitHub

            // TODO: Añadir lógica para resetear los cambios en el interfaz: desactivar campo de envío,
            // resetear mensaje de error, mostrar lista de repositorios,...

            // Obtener datos de autenticación de usuario para hacer peticiones
            // autenticadas a la API de GitHub
            var userAuth = process.env.VUE_APP_USERNAME || "Ainhoaleft";
            var passAuth = process.env.VUE_APP_USERTOKEN || "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";

            // TODO: realizar petición fetch par obtener los datos y mostrar la información en la página
            // Ejemplo de paso de datos de autorización con fetch: https://stackoverflow.com/questions/43842793/basic-authentication-with-fetch
            let url = 'https://api.github.com/users/{{user}}';
            fetch(url,{method:'GET'})
            .then(response => response.json())
            .then(data =>{
                let avatar_url = data.avatar_url
                let login = data.login
                let html_url = data.html_url
                let repos_url = data.repos_url
                
            });
        },
        obtenerRepositorios: function() {
            // TODO: Función para obtener los repositorios del usuario desde la API de GítHub
            // La URL de los repositorios de usuario se puede obtener a través del campo 'repos_url' de los datos del usuario

            // Obtener datos de autenticación de usuario para hacer peticiones
            // autenticadas a la API de GitHub
            var userAuth = process.env.VUE_APP_USERNAME || "Ainhoaleft";
            var passAuth = process.env.VUE_APP_USERTOKEN || "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";


            // TODO: realizar petición fetch par obtener los datos y mostrar la información en la página
            // Ejemplo de paso de datos de autorización con fetch: https://stackoverflow.com/questions/43842793/basic-authentication-with-fetch
            let url = 'https://api.github.com/users/{{user}}/repos';
            let username = 'user';
            let password = 'pass';
    
            //headers.append('Content-Type', 'text/json');

            fetch(url,{method:'GET', 
            headers: {'Authorization': 'Basic ' + btoa('login:password')}})
            .then(response => response.json())
            .then(data =>{
                this.user = data
                let full_name = data.full_name  
                let html_url = data.html_url
                let description = data.description
                let forks_count = data.forks_count
                
            });
        }
    }
}

</script>

<style scoped>
</style>
