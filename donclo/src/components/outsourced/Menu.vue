<script setup>
    import MenuInhalt from './MenuInhalt.vue'
</script>

<template>

    <nav class="navbar offcanvas-left">


        <button class="navbar-toggler btn btn-primary d-md-none" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasNavbar" aria-controls="offcanvasNavbar" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="d-none d-md-block">
            <MenuInhalt></MenuInhalt>
        </div>

        <div class="offcanvas offcanvas-top" tabindex="-1" id="offcanvasNavbar" aria-labelledby="offcanvasTopLabel">
            <div class="offcanvas-header">
                <h5 class="offcanvas-title" id="offcanvasTopLabel">Offcanvas top</h5>
                <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
            </div>
            <div class="offcanvas-body">
                <MenuInhalt></MenuInhalt>
            </div>
        </div>

    </nav>

</template>