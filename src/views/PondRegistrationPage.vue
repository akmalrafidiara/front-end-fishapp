<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button :text="getBackButtonText()" default-href="/tabs/ponds"></ion-back-button>
          <h3 class="section-title" style="margin-right: 10px;">Registrasi Kolam</h3>  
        </ion-buttons>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <div class="status">
        <ion-list>
          <ion-item>
            <ion-label position="stacked">Nama Kolam</ion-label>
            <ion-input placeholder="Kolam 1" v-model="name"></ion-input>
          </ion-item>
        </ion-list>
        <ion-list>
          <ion-item>
            <ion-label position="stacked">Lokasi Kolam</ion-label>
            <ion-input placeholder="Block A" v-model="location"></ion-input>
          </ion-item>
        </ion-list>
        <ion-list>
          <ion-item>
            <ion-label position="stacked">Material Kolam</ion-label>
            <ion-select interface="action-sheet" v-model="material">
              <ion-select-option value="1">Tanah</ion-select-option>
              <ion-select-option value="2">Beton</ion-select-option>
              <ion-select-option value="3">Terpal</ion-select-option>
              <!-- <ion-select-option  v-for="material in material_options" :value="material.key">{{material.value}}</ion-select-option> -->
            </ion-select>
          </ion-item>
        </ion-list>
        <ion-list>
          <ion-item>
            <ion-label position="stacked">Bentuk Kolam</ion-label>
            <ion-select interface="action-sheet" v-model="shape">
              <ion-select-option value="1">Kotak</ion-select-option>
              <ion-select-option value="2">Bundar</ion-select-option>
              <!-- <ion-select-option  v-for="shape in shape_options" :value="shape.key">{{shape.value}}</ion-select-option> -->
            </ion-select>
          </ion-item>
        </ion-list>
        <ion-list>
          <!-- @click.prevent="getFormValues()" -->
          <ion-button expand="block" color="tertiary" @click.prevent="getFormValues()">Registrasi</ion-button>
        </ion-list>
        <ion-list>
          <h1>{{ name }}</h1>
          <h4>{{ location }}</h4>
          <h5>{{ material }}</h5>
          <h5>{{ shape }}</h5>
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonPage, IonHeader, IonButtons, IonButton, IonBackButton, IonToolbar, IonList, IonInput, IonLabel, IonItem, IonSelect, IonSelectOption  } from '@ionic/vue';
import { defineComponent } from 'vue';
import { add } from 'ionicons/icons';
import axios from 'axios';


export default defineComponent({
  name: 'PondRegisrationPage',
  data() {
    return {
      name: '',
      location: '',
      material: '',
      shape: '',
      material_options: [
        {key: 'tanah', value: 1},
        {key: 'beton', value: 2},
        {key: 'terpal', value: 3}
      ],
      shape_options: [
        {key: 'kotak', value: 1},
        {key: 'bundar', value: 2}
      ],
      getBackButtonText: () => {
        const win = window as any;
        const mode = win && win.Ionic && win.Ionic.mode;
        return mode === 'ios' ? 'Back' : '';
      }
    }
  },
  components: {
    IonContent, IonPage, IonHeader, IonButtons, IonButton, IonBackButton, IonToolbar, IonList, IonInput, IonLabel, IonItem, IonSelect, IonSelectOption
  },
  setup() {
    return {
      add
    }
  }, 
  methods: {
    getFormValues (){
      // console.log(this.name)
      // console.log(this.location)
      // console.log(this.material)
      // console.log(this.shape)

      let pond = {
        'name' : this.name,
        'location' : this.location,
        'material' : this.material,
        'shape' : this.shape
      }
      console.log(pond)
      axios.post("http://127.0.0.1:5000/pond", pond)

      document.location = ('/tabs/ponds')
    }
  }
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
* {
  font-family: 'Poppins', sans-serif;
}
ion-content{
  --ion-background-color:#1F1D2B;
}s
.section-title {
  margin-left: 12px;
  font-weight: bold;
  margin-top: 20px;
  text-align: center;
}
.kolam-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px 12px;
  font-weight: bold;
}
.kolam-header img {
  width: 30px;
}
.kolam-header img:nth-child(2) {
  filter: invert(100%);
}
.card-pond {
  background-color: #fff;
  color: #000;
  width: 100%;
  padding: 20px 15px;
  border-radius: 15px;
  margin-bottom: 20px;
}
.header-pond {
  display: flex;
  justify-content: space-between;
  font-weight: bold;
  align-items: center;
  border-bottom: 3px solid #333;
}
.header-pond h3 {
  font-weight: bold;
  font-size: 25px;
}
.header-pond p {
  padding: 10px 15px;
  border-radius: 5px;
  font-size: 20px;
  color: #fff;
}
.content-pond {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: -20px;
}
.content-pond img {
  height: 30px;
}
.green {
  background-color: #1B7C1A;
}
.red {
  background-color: #952229;
}

</style>
