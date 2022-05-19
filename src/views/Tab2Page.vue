<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 2</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 2</ion-title>
        </ion-toolbar>
      </ion-header>
      <div class="container" >
      <capacitor-google-map id="map" ref="mapDivRef" ></capacitor-google-map>
      <button @click="newMap">Create Map</button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script >
import { defineComponent,ref } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import { GoogleMap } from '@capacitor/google-maps';
//const apiKey = process.env.MY_MAPS_API_KEY;





export default defineComponent({
  name: 'Tab2Page',
   
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage },
  setup() { 
    
    
  const createMap = async () => {
    const mapRef = document.getElementById('map');

    await GoogleMap.create({
      id: 'my-map', // Unique identifier for this map instance
      element: mapRef, // reference to the capacitor-google-map element
      apiKey: process.env.MY_MAPS_API_KEY, // Your Google Maps API Key
      config: {
        center: {
          // The initial position to be rendered by the map
          lat: 33.6,
          lng: -117.9,
        },
        zoom: 8, // The initial zoom level to be rendered by the map
      },
    });
  };

  return {
    createMap
  }
  } ,
  
});
</script>

<style>
  capacitor-google-map {
    display: inline-block;
    width: 275px;
    height: 400px;
  }
</style>
