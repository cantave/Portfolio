<template>

    <div>
        <div v-if="isLoading">Loading...</div>
        <div >
            <repo-component 
            v-for="project in repos" 
            :key="project.id" 
            :title="project.name" 
            :htmlUrl="project.html_url" 
            :description ="project.description"
            :id="project.id">
            </repo-component>
        </div>
    </div>
</template>

<script>
import GitHubService from '@/services/GitHubService';
import RepoComponent from '@/components/RepoComponent.vue';


export default {
    components: { RepoComponent },
    data() {
        return {
            repos: [],
            isLoading: true
        };
    },
    created() {
        GitHubService.getRepos()
            .then((response) => {
                //console.log(response.data);
                this.repos = response.data;
                this.isLoading = false;
            })
            .catch((error) => {
                console.error('Error fetching repos:', error);
                this.isLoading = false;
            });
    }
};
</script>

<style scoped>
.repos {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 1rem;
}
</style>