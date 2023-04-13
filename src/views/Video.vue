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
import casteaching from "@acacha/casteaching";
const api = casteaching({baseUrl:'http://casteaching.test/api'})
// const api = casteaching({baseUrl:'http://casteaching.aleixcarles.me/api'})
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
        this.video = await api.video.show(this.$route.params.id)
        // this.video = {
        //   "id": 2,
        //   "title": "Video 1",
        //   "description": "Descripcio video 1",
        //   "url": "https://www.youtube.com/embed/a4ez0CcEHV4",
        //   "published_at": null,
        //   "previous": null,
        //   "next": null,
        //   "series_id": null,
        //   "created_at": "2023-03-02T15:01:38.000000Z",
        //   "updated_at": "2023-03-02T15:01:38.000000Z"
        // }
    }
}
</script>

<style scoped>
#video {
    width: 100%;
    height: 70vh;
}
</style>