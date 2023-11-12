<script setup>
    import { ref } from 'vue'
    const abholungRadioButton = ref(true)
    const daten = ref(String)
    
    defineProps({
        finalVorname: String,
        finalNachname: String,
        finalArtKleidung: String,
        finalKrisengebiet: String,
        finalStrasse: String,
        finalHausNr: String,
        finalPLZ: String,
        abholung: String
    })
    defineEmits(['update:finalVorname', 'update:finalNachname', 'update:finalArtKleidung', 'update:finalKrisengebiet', 'update:finalStrasse', 'update:finalHausNr','update:finalPLZ' , 'update:abholung'])

    function ueberpruefen(eingabe) {
        this.daten = eingabe

        this.daten = this.daten.replaceAll('<', ' ')
        this.daten = this.daten.replaceAll('>', ' ')
        this.daten = this.daten.replaceAll('/', ' ')

        return daten.value
    }



</script>

<template>
    <div class="container-fluid">
        <div class="row-fluid">

            <input class="col-auto" type="radio" :value=true v-model="abholungRadioButton" @input="$emit('update:abholung' , 'abholung')" />
            <p class="col">Abholung</p>

            <input class="col-auto" type="radio" :value=false v-model="abholungRadioButton" @input="$emit('update:abholung' , 'abgabe')" />
            <p class="col">Abgabe an der Gesch&auml;fstelle</p>
        </div>
        <!--Formular f�r die Abgabe-->

        <div class="row-fluid">
            <form>
                <div class="col-auto">
                    <div class="form-floating mb-3">
                        <input type="text" class="form-control" id="artKleidung" @input="$emit('update:finalArtKleidung' , ueberpruefen($event.target.value))">
                        <label for="artKleidung">Art der Kleidung</label>
                    </div>
                </div>
                <div class="col-auto">
                    <div class="form-floating">
                        <select class="form-select" id="floatingSelectDisabled" aria-label="Floating label disabled select example" @input="$emit('update:finalKrisengebiet' , $event.target.value)">
                            <option selected>W&auml;hlen sie das Krisengebiet aus, welches sie unterst&uuml;tzen wollen</option>
                            <option value="Afghanistan">Afghanistan</option>
                            <option value="Irak">Irak</option>
                            <option value="Jemen">Jemen</option>
                            <option value="Mali">Mali</option>
                            <option value="Niger">Niger</option>
                            <option value="Nigeria">Nigeria</option>
                            <option value="Pakistan">Pakistan</option>
                            <option value="Somalia">Somalia</option>
                            <option value="Sudan">Sudan</option>
                            <option value="Syrien">Syrien</option>
                            <option value="Tschad">Tschad</option>
                            <option value="Ukraine">Ukraine</option>
                        </select>
                        <label for="floatingSelectDisabled">Krisengebiet</label>
                    </div>
                </div>
            </form>
        </div>





        <!-- Formular f�r die Abholung-->
        <div class="row-fluid">
            <br>
            <form v-if="abholungRadioButton">
                <div class="row">
                    <div class="col-auto">
                        <div class="form-floating mb-3">
                            <input type="text" class="form-control" id="vorname" @input="$emit('update:finalVorname' , ueberpruefen($event.target.value))">
                            <label for="vorname">Vorname</label>
                        </div>
                    </div>
                    <div class="col-auto">
                        <div class="form-floating mb-3">
                            <input type="text" class="form-control" id="nachname" @input="$emit('update:finalNachname' , ueberpruefen($event.target.value))">
                            <label for="nachname">Nachname</label>
                        </div>
                    </div>
                </div>
                <div class="row-fluid">
                    <div class="col-auto">
                        <div class="form-floating mb-3">
                            <input type="text" class="form-control" id="strasse"  @input="$emit('update:finalStrasse' , ueberpruefen($event.target.value))">
                            <label for="strasse">Stra&szlig;e</label>
                        </div>
                    </div>
                    <div class="col-auto">
                        <div class="form-floating mb-3">
                            <input type="text" class="form-control" id="hausnummer" @input="$emit('update:finalHausNr' , ueberpruefen($event.target.value))">
                            <label for="hausnummer">Hausnummer</label>
                        </div>
                    </div>
                    <div class="col-auto">
                        <div class="form-floating mb-3">
                            <input type="text" class="form-control" id="plz" @input="$emit('update:finalPLZ' , ueberpruefen($event.target.value))">
                            <label for="plz">Postleitzahl</label>
                        </div>
                    </div>
                </div>
            </form>
        </div>
    </div>

</template>