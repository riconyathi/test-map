<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div class="map" ref="mapDivRef">
        
      </div>
    </ion-content>
  </ion-page>
</template>

<script >
import { defineComponent, ref} from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';


export default  defineComponent({
  name: 'Tab1Page',
  setup(){
    const map = ref(null);
    const mapDivRef = ref(null);

    const key = "";

    const googleMapScript = document.createElement("SCRIPT");
    
    googleMapScript.setAttribute(
      "src",
      `https://maps.googleapis.com/maps/api/js?key=${key}&callback=initMap`
    );
    googleMapScript.setAttribute("defer","");
    googleMapScript.setAttribute("async","");
    document.head.appendChild(googleMapScript);
 
     window.initMap = () => {

          map.value = new window.google.maps.Map(mapDivRef.value, {
           mapTypeId : "roadmap",
           zoom : 15,
           disableDefaultUI : false,
           center : { lat : -25.953960 , lng : 28.142630 }

          });
    };

    return {
      mapDivRef
    }
  },
  components: {  IonHeader, IonToolbar, IonTitle, IonContent, IonPage }
});
</script>

<style>
  .map {
    width: 100%;
    height : 100%;
    background-color: rgb(199, 99, 33);
  }
</style>
