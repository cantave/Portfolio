<template>
    <div class="project-filter">
        <input type="text" 
        v-model="searchTerm" 
        placeholder="Search projects..."
        @input="$emit('update:search', searchTerm)" />
        <select v-model="selectedFilter" @change="$emit('update:filter', selectedFilter)">
            <option value="Newest">Newest</option>
            <option value="Oldest">Oldest</option>
            <option value="projectType">Project Type</option>
        </select>
    </div>
</template>

<script>
export default {
    props: {
        searchTerm: {
            type: String,
            default: ''
        },
        selectedFilter: {
            type: String,
            default: 'Newest'
        }
    },
    data() {
        return {
            // eslint-disable-next-line vue/no-dupe-keys
            searchTerm: this.searchTerm,
            // eslint-disable-next-line vue/no-dupe-keys
            selectedFilter: this.selectedFilter
        };
    }
};
</script>

<style scoped>
.project-filter {
    margin-bottom: 1rem;
    margin-top: 1rem;
}

.project-filter input {
    margin-right: 1rem;
    background-color: whitesmoke;
    font-family: 'Oswald', sans-serif;
    border-radius: 8px;
}

.project-filter select {
    font-family: 'Oswald', sans-serif;
    background-color: whitesmoke;
    border-radius: 8px;
}
</style>