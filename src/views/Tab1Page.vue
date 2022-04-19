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

      <ion-button @click="setIsOpen"> Open Modal </ion-button>

      <IonModal
        trigger="open-modal"
        :isOpen="isOpen"
        @onDidDismiss="() => onDissmiss()"
      >
        <IonContent force-overscroll="false"> </IonContent>
      </IonModal>

      <ExploreContainer name="Tab 1 page" />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButton,
  IonModal,
} from "@ionic/vue";
import ExploreContainer from "@/components/ExploreContainer.vue";

export default defineComponent({
  name: "Tab1Page",
  components: {
    ExploreContainer,
    IonModal,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonButton,
  },
  setup() {
    const isOpen = ref(false);

    const setIsOpen = () => {
      isOpen.value = true;
    };

    const setIsClosed = () => {
      isOpen.value = false;
    };

    const onDissmiss = () => {
      console.log("HERE");
    };

    return {
      isOpen,
      setIsOpen,
      setIsClosed,
      onDissmiss,
    };
  },
});
</script>

<style scoped>
.ion-content {
  --background: #f2f2f7;
}

ion-modal {
  --width: 290px;
  --height: 295px;
  --border-radius: 8px;
}
</style>
