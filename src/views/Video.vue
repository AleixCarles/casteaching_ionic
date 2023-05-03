<template>
    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-menu-button color="primary"></ion-menu-button>
                </ion-buttons>
                <ion-title>{{ video.title }}</ion-title>
            </ion-toolbar>
        </ion-header>

        <ion-content :fullscreen="true">
            <ion-header collapse="condense">
                <ion-toolbar>
                    <ion-title size="large">Video {{ $route.params.id }}</ion-title>
                </ion-toolbar>
            </ion-header>

            <div id="container">
                <iframe id="video" width="560" height="315" :src="video.url" title="YouTube video player"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                        allowfullscreen></iframe>
                <ion-card>
                    <ion-card-header>
                        <ion-card-title>
                            {{ video.title }}
                        </ion-card-title>
                        <ion-card-subtitle>
                            {{ video.published_at }}
                        </ion-card-subtitle>
                    </ion-card-header>
                    <ion-card-content>
                        {{ video.description }}
                    </ion-card-content>
                </ion-card>
            </div>
        </ion-content>
    </ion-page>
</template>

<script>
import {
    IonButtons,
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardSubtitle,
    IonCardTitle,
    IonContent,
    IonHeader,
    IonMenuButton,
    IonPage,
    IonTitle,
    IonToolbar
} from '@ionic/vue';

export default {
    name: 'Video',
    components: {
        IonButtons,
        IonContent,
        IonHeader,
        IonCardSubtitle,
        IonCardContent,
        IonCard,
        IonCardTitle,
        IonCardHeader,
        IonMenuButton,
        IonPage,
        IonTitle,
        IonToolbar
    },
    data () {
        return {
            video: {},
        }
    },
    async created() {
        try {
            this.video = await this.casteaching.video.show(this.$route.params.id)
        }catch (error){
            console.log(error)
        }

    }
}
</script>

<style scoped>

#video {
    width: 100%;
    height: 70vh;
}
</style>