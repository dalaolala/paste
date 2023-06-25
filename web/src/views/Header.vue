<template>
    <b-row>
        <b-col md="12">
            <b-navbar toggleable="md" variant="dark" type="dark" fixed="top">
                <router-link class="navbar-brand" to="/" :title="$t('lang.nav.router_link')">代码便利贴</router-link>
            </b-navbar>
            <b-popover target="github-icon" placement="auto" triggers="hover">
                <div class="text-center">
                    {{ $t('lang.nav.beg') }}
                </div>
            </b-popover>
        </b-col>
    </b-row>
</template>

<script>
    export default {
        name: "Header",
        methods: {
            onSubmit() {
                this.$router.push(this.key);
                this.key = null;
            }
        }
    }
</script>

<style scoped>
    .width {
        max-width: 300px;
    }
</style>
