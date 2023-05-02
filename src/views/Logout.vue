<template>

    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-menu-button color="primary"></ion-menu-button>
                </ion-buttons>
                <ion-title>Login</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content :fullscreen="true">

            <ion-card>
                <ion-card-header>
                    <ion-card-subtitle>Please login</ion-card-subtitle>
                </ion-card-header>
                <ion-card-content>

                    <ion-button @click="logout">Logout</ion-button>
                </ion-card-content>
            </ion-card>
        </ion-content>
    </ion-page>
</template>

<script>
import store from "../store";

import {
    IonButton, IonButtons,
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardSubtitle, IonContent, IonHeader,
    IonMenuButton, IonPage, IonTitle, IonToolbar
} from "@ionic/vue";

export default {
    name: 'Logout',
    components: {
        IonContent,
        IonToolbar,
        IonPage,
        IonHeader,
        IonTitle,
        IonMenuButton,
        IonButtons,
        IonCard, IonCardHeader, IonCardContent, IonButton, IonCardSubtitle,
    },
    methods:{
        async logout(){
            console.log('logout');
            await store.set('token', null)
            const oldUser = await store.get('user')
            await store.set('user', null)
            this.emitter.emit('logout',oldUser)

            this.$router.push('/login')
        }
    }
}

</script>