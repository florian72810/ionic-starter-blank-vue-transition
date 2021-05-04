<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-button
        @click="openModal"
      >
        Open Modal
      </ion-button>

      <ion-button
        @click="openLoader"
      >
        Open Loading
      </ion-button>

      <ion-button
        @click="openAction"
      >
        Open Action Sheet
      </ion-button>
    
      <div id="container">
        <strong>Ready to create an app?</strong>
        <p>Start with Ionic <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI Components</a></p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, modalController, loadingController, actionSheetController, iosTransitionAnimation } from '@ionic/vue';
import { defineComponent } from 'vue';
import ExampleModalVue from './ExampleModal.vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonButton
  },
  methods: {
    openModal(): void {
      modalController.create({
        component: ExampleModalVue,
        enterAnimation: iosTransitionAnimation,
        leaveAnimation: iosTransitionAnimation
      }).then(modal => modal.present());
    },
    openLoader(): void {
      loadingController.create({
        duration: 3000,
        message: "3s loader"
      }).then(loading => loading.present());
    },
    openAction(): void {
      actionSheetController.create({
        header: "Demo",
        buttons: [
          {
              text: 'Delete',
              role: 'destructive',
              handler: () => {
                console.log('Delete clicked')
              },
            }
        ]
      }).then(action => action.present());
    }
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>