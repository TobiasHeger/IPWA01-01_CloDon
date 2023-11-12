<script setup>
    import Menu from './outsourced/Menu.vue'
    import Dummy from './DummyKomponente.vue'

    function suche(eingabe) {
        eingabe = eingabe.replaceAll('<', ' ')
        eingabe = eingabe.replaceAll('>', ' ')
        eingabe = eingabe.replaceAll('/', ' ')
        location.hash = '/Dummy'
    }
</script>
<template>

    <div class="container-fluid border bg-success">
        <br />
        <div class="row">
            <div class="col-auto align-self-start">
                <img alt="DonClo logo" class="img-fluid height:auto min-width:50%" src="../assets/logo.png" />
            </div>
            <h1 class="col-auto align-self-center">
                CloDon
            </h1>
        </div>
        <div class="row justify-content-between">
            <Menu class="col-auto"></Menu>

            <form class="col-auto" role="search">
                <input type="search" class="form-control" placeholder="Suche..." aria-label="Search" @keyup.enter="suche($event.target.value)">


            </form>
        </div>
        <br />
    </div>
</template>
