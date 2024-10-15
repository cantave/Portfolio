<template>

    <div>
        <filter-component :searchTerm="searchTerm" :selectedFilter="selectedFilter" @update:search="searchTerm = $event"
            @update:filter="selectedFilter = $event" />
        <div v-if="isLoading">Loading...</div>
        <div>
            <repo-component v-for="project in filteredRepos" :key="project.id" :title="project.name" :htmlUrl="project.html_url"
                :description="project.description" :id="project.id">
            </repo-component>
        </div>
    </div>
</template>

<script>
import GitHubService from '@/services/GitHubService';
import RepoComponent from '@/components/RepoComponent.vue';
import FilterComponent from '@/components/FilterComponent.vue';


export default {
    components: { RepoComponent, FilterComponent },
    data() {
        return {
            repos: [],
            isLoading: true,
            searchTerm: '',
            selectedFilter: 'Newest',
        };
    },
    computed: {
        filteredRepos() {
            return this.repos
            .filter(repo => 
                repo.name.toLowerCase().includes(this.searchTerm.toLowerCase()) ||
                (repo.description && repo.description.toLowerCase().includes(this.searchTerm.toLowerCase()))
            )
            .sort((a,b) => {
                if(this.selectedFilter === 'Newest') {
                    return new Date(b.updated_at) - new Date(a.updated_at);
                } else if (this.selectedFilter == 'Oldest') {
                    return new Date(a.updated_at) - new Date(b.updated_at);
                }
                return 0;
            });
        },
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