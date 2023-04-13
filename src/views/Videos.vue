<template>
    <ion-list>
        <ion-list-header>
            Recent Conversations
        </ion-list-header>

        <ion-item v-for="video in videos" :key="video.message">
            <ion-avatar slot="start">
                <img src="https://via.placeholder.com/80">
            </ion-avatar>
            <ion-label>
                <h2>{{ video.title }}</h2>
                <p>{{ video.description}}</p>
            </ion-label>
        </ion-item>

    </ion-list>
</template>

<script>
import {IonList, IonItem, IonListHeader, IonAvatar, IonLabel} from "@ionic/vue";
import casteaching from "@acacha/casteaching";
const api = casteaching({baseUrl:'http://casteaching.test/api'})
export default {
    name: "Videos",
    components: {
        IonList,
        IonItem,
        IonListHeader,
        IonAvatar,
        IonLabel
    },
    data(){
        return{
            videos: []
        }
    },
    async created() {
        this.videos = await api.videos()
    }
}
</script>

<style scoped>

</style>