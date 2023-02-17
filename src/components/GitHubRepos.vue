<template>
    <div>
        <div class="list-group">
            <a href="#" class="list-group-item list-group-item-action active">
                Repositorios de {{ username }}
            </a>
            <a href="#" class="list-group-item list-group-item-action active"></a>
            <a href="#" class="list-group-item list-group-item-action active"></a>
            <a href="#" class="list-group-item list-group-item-action active"></a>
        </div>
        <!-- TODO: Crear componente GitHubRepos -->
    </div>
</template>

<script>
export default {
    name: 'GitHubRepos',
    props: [
        // TODO: crear parámetro 'repolist'
    ],
}
</script>

<style scoped>
</style>
