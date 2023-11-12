<script setup>
    import { ref, computed } from 'vue'
    import HeaderKomponente from './components/HeaderKomponente.vue'
    import StartseiteKomponente from './components/StartseiteKomponente.vue'
    import SpendenseiteKomponente from './components/SpendenseiteKomponente.vue'
    import FooterKomponente from './components/FooterKomponente.vue'
    import DummyKomponente from './components/DummyKomponente.vue'

    const routes = {
        '/': StartseiteKomponente,
        '/Spendenseite': SpendenseiteKomponente,
        '/Dummy': DummyKomponente
    }

    const currentPath = ref(window.location.hash)

    window.addEventListener('hashchange', () => {
        currentPath.value = window.location.hash
    })

    const currentView = computed(() => {
        return routes[currentPath.value.slice(1) || '/'] || NotFound
    })


</script>

<template>
    <header>
        <HeaderKomponente></HeaderKomponente>
    </header>

    <main>
        <component :is="currentView" />
    </main>
    
    <footer>
        <FooterKomponente></FooterKomponente>
    </footer>
</template>


