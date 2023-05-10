<template>
    <div>
        <select class="selectpicker" data-width="fit">
            <option data-content='<span class="flag-icon flag-icon-us"></span> English'>English</option>
            <option data-content='<span class="flag-icon flag-icon-mx"></span> Español'>Español</option>
        </select>
        <button @click="changeLanguage('en')">English</button>
        <button @click="changeLanguage('es')">Español</button>
        <h1>{{ message }}</h1>
        <!-- Rest of the blog content -->
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: '',
        };
    },
    methods: {
        changeLanguage(lang) {
            axios.get(`/api/welcome-message?lang=${lang}`).then((response) => {
                this.message = response.data.message;
            });
        },
    },
    created() {
        axios.get('/api/welcome-message').then((response) => {
            this.message = response.data.message;
        });
    },
};
</script>
