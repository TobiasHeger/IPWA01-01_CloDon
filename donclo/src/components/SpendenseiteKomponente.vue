<script setup>
    import FormularKleiderspende from './outsourced/FormularKleiderspende.vue'
    import { ref, reactive } from 'vue'


    const formularAbgeschickt = ref(false)
    const finalVorname = ref(null)
    const finalNachname = ref(null)
    const finalArtKleidung = ref(null)
    const finalKrisengebiet = ref(null)
    const finalStrasse = ref(null)
    const finalHausNr = ref(null)
    const finalPLZ = ref(null)
    const abholung = ref('abholung')
    const kleiderspende = reactive({})
    var datumZeit = ref()

    function formularSenden(abholung) {
        
        datumZeit = new Date().toLocaleString("de-DE");
        let felderBefuelt = true

        if (abholung == 'abholung') {

            kleiderspende.Registrierungszeit = datumZeit;
            kleiderspende.Vorname = finalVorname;
            kleiderspende.Nachname = finalNachname;
            kleiderspende.Kleidungsart = finalArtKleidung;
            kleiderspende.Krisengebiet = finalKrisengebiet;
            kleiderspende.Strasse = finalStrasse;
            kleiderspende.HausNr = finalHausNr;
            kleiderspende.PLZ = finalPLZ;


            
            const plzLaenge = 5

            for (let key in kleiderspende) {
                
                if (!kleiderspende[key]) {
                    alert('Bef&uuml;lle das Feld ' + key)
                    felderBefuelt = false
                }
                
            }



            if (kleiderspende.PLZ.length == 5) {
                if (!kleiderspende.PLZ.startsWith('38')) {
                    alert('PLZ liegt nicht im Abholgebiet. PLZ muss mit 38 beginnen.')
                } else if (felderBefuelt) {
                    formularAbgeschickt.value = true;
                   
                    return kleiderspende
                }
            } else { alert('PLZ ist nicht g&uuml;ltig') }

        } else{

            kleiderspende.Registrierungszeit = datumZeit;
            kleiderspende.Kleidungsart = finalArtKleidung;
            kleiderspende.Krisengebiet = finalKrisengebiet;



            let felderBefuelt = true

            for (let key in kleiderspende) {
                
                if (!kleiderspende[key]) {
                    alert('Befülle das Feld ' + key)
                    felderBefuelt = false
                }
               
            }


             if (felderBefuelt) {
                 formularAbgeschickt.value = true;
                 
                    return kleiderspende
                }

        }
    }
</script>

<template>
    <div class="container border-start border-end" v-if="!formularAbgeschickt">
        <br />
        <div class="row-sm-8 justify-content-center">
            <h1 class="col-auto">
                Kleiderspende
            </h1>
        </div>
        <div class="row-sm-8 justify-content-center">
            <p class="col-auto">
                Hier kannst du dich mit deiner Kleiderspende registrien. Dazu f&uuml;lle einfach das Formular aus und dr&uuml;cke auf senden.
            </p>
        </div>
        <div class="row-sm-8 justify-content-center">
            <h4 class="col-auto">Formular</h4>
        </div>
        <div class="row-sm-8">
            <FormularKleiderspende class="col-auto" v-model:finalVorname="finalVorname" v-model:finalNachname="finalNachname" v-model:finalArtKleidung="finalArtKleidung" v-model:finalKrisengebiet="finalKrisengebiet" v-model:finalStrasse="finalStrasse" v-model:finalHausNr="finalHausNr" v-model:finalPLZ="finalPLZ" v-model:abholung="abholung"></FormularKleiderspende>
        </div>
        <div class="row-sm-8 justify-content-center">
            <button class="button" @click="formularSenden(abholung)">Senden</button>
        </div>
    </div>

    <div class="container border-start border-end" v-if="formularAbgeschickt">
        <div class="row-sm-8 justify-content-center">
            <h4 class="col-auto"> Ihre Registrierung war erfolgreich!</h4>
        </div>
        <div class="row-sm-8 justify-content-center">
            <p class="col-auto"> Danke f&uuml;r Ihre Spende. Bitte &uuml;berpr&uuml;fen Sie Ihre Daten.</p>
        </div>
        <div class="row-sm-8 justify-content-center">
            <ul class="list-group">
                <li class="list-group-item" v-for="(value, key) in kleiderspende">
                    {{key}} : {{value}}
                </li>
            </ul>

        </div>
    </div>
</template>