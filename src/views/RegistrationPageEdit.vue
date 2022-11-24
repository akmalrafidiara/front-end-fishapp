<template>
	<ion-page>
		<ion-content>
			<div class="kolam-header" style="margin-inline: 30px;">
				<div class="back-btn">
					<a href="/tabs/pondspage"> &lt; </a>
				</div>
				<div>
					<h2 style="margin-right: 200px;">Edit Registrasi Kolam</h2>
				</div>
			</div>
		</ion-content>
	</ion-page>
	<div style="margin-top: 100px;">
		<ion-card class="box">
			<ion-card-header>
				<ion-label style="color: white">Nama Kolam</ion-label>
			</ion-card-header>

			<ion-card-content>
				<ion-input v-model="nama" placeholder="Kolam 1" style="background-color: black;"></ion-input>
			</ion-card-content>
		</ion-card>
		<ion-card class="box">
			<ion-card-header>
				<ion-label style="color: white">Lokasi Kolam</ion-label>
			</ion-card-header>

			<ion-card-content>
				<ion-input v-model="lokasi" placeholder="Blok A" style="background-color: black;"></ion-input>
			</ion-card-content>
		</ion-card>
		<ion-card class="box">
			<ion-card-header>
				<ion-label style="color: white">Material Kolam</ion-label>
				<ion-select v-model="material" interface="action-sheet">
					<ion-select-option value="tanah">Tanah</ion-select-option>
					<ion-select-option value="beton">Beton</ion-select-option>
					<ion-select-option value="terpal">Terpal</ion-select-option>
				</ion-select>
			</ion-card-header>
		</ion-card>
		<ion-card class="box">
			<ion-card-header>
				<ion-label style="color: white">Bentuk Kolam</ion-label>
				<ion-select v-model="bentuk" interface="action-sheet">
					<ion-select-option value="kotak">Kotak</ion-select-option>
					<ion-select-option value="bundar">Bundar</ion-select-option>
				</ion-select>
			</ion-card-header>
		</ion-card>
        <ion-card class="box">
			<ion-card-header>
				<ion-label style="color: white">Diamater (m)</ion-label>
			</ion-card-header>

			<ion-card-content>
				<ion-input v-model="diameter" placeholder="12 m" style="background-color: black;"></ion-input>
			</ion-card-content>
		</ion-card>
        <ion-card class="box">
			<ion-card-header>
				<ion-label style="color: white">Tinggi (m)</ion-label>
			</ion-card-header>

			<ion-card-content>
				<ion-input v-model="tinggi" placeholder="3 m" style="background-color: black;"></ion-input>
			</ion-card-content>
		</ion-card>
		<ion-list>
			<ion-button name="registration" expand="block" color="secondary" @click="getFormValues()">Registrasi
			</ion-button>
		</ion-list>
	</div>

</template>
  
<script lang="ts">
import { IonInput, IonLabel, IonList, IonPage, IonContent, IonSelect, IonSelectOption } from '@ionic/vue';
import { defineComponent } from 'vue';
import { Storage } from '@ionic/storage';


export default defineComponent({
	name: "RegFormEdit",
	components: { IonInput, /*IonItem*/ IonLabel, IonList, IonPage, IonContent, IonSelect, IonSelectOption },
	setup() {
		const store = new Storage();
		store.create();
		return {  }
	}, data() {
		return {
			nama: '',
			lokasi: '',
			material: '',
			bentuk: '',
            diameter: '',
            tinggi: ''
		}
	},
	methods: {
		getFormValues() {
			const obj = ['name:', this.nama, 'location:', this.lokasi, 'material:', this.material, 'shape:', this.bentuk, 'diameter:', this.diameter, 'height:', this.tinggi]
			console.log(obj)
		},
	}
});
</script>

<style scoped>
.kolam-header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin: 15px 12px;
	font-weight: bold;
}

.kolam-header img {
	width: 30px;
}
</style>