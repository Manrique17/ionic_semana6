<template>
    <ion-page>
        <ion-header>
            <ion-toolbar>
               
                <ion-title>Juegos</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
            <ion-card>
                <ion-card-header>
                    <ion-card-title>Juegos de {{ this.$route.params.consola }}</ion-card-title>
                    <ion-card-subtitle>Listado de videojuegos</ion-card-subtitle>
                </ion-card-header>
                <ion-card-content>
                    <ion-list lines="none">
                        <template v-for="(juego, i) in juegos" :key="i">
                            <ion-item v-if="juego.consola == this.$route.params.consola">
                                <ion-thumbnail>
                                    <img :src="juego.imagen" alt="portada">
                                </ion-thumbnail>
                                <ion-label>{{ juego.nombre }}</ion-label>
                                <ion-button fill="clear" color="danger" @click="showAlert(true, i)">
                                    <ion-icon :icon="heart"></ion-icon>
                                </ion-button>
                                <ion-button fill="clear" color="warning" @click="showToast(true, i)">
                                    <ion-icon :icon="addCircle"></ion-icon>
                                </ion-button>
                            </ion-item>
                            <ion-alert
                                header="Notificacion"
                                sub-header="Exito!"
                                message="Juego agregado a favoritos"
                                :is-open="alertState[i]"
                                @didDismiss="showAlert(false, i)">
                            </ion-alert>
                            <ion-toast 
                                header="Notificacion"
                                sub-header="Exito!"
                                message="Juego agregado a favoritos"
                                :is-open="toastState[i]"
                                @didDismiss="showToast(false, i)"
                                :duration="2000"
                            />

                        </template>
                    </ion-list>
                </ion-card-content>
            </ion-card>
        </ion-content>
    </ion-page>
        
    
</template>


<script>
import { heart, addCircle} from 'ionicons/icons'
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButtons, 
        IonBackButton, IonCard, IonCardHeader, IonCardTitle, IonCardSubtitle, 
        IonCardContent, IonList, IonThumbnail, IonLabel, IonItem, 
        IonIcon, IonAlert, IonToast, IonButton} from '@ionic/vue'

export default{
    name: 'Juegos', 
    component: {
        IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButtons, 
        IonBackButton, IonCard, IonCardHeader, IonCardTitle, IonCardSubtitle, 
        IonCardContent, IonList, IonThumbnail, IonLabel, IonItem, IonIcon, 
        IonAlert, IonToast, IonButton
    }, 
    data(){
        return {
            heart, addCircle,
            alertState: [], 
            toastState:[],
            juegos: [

                {
                    consola: "PlayStations",
                    nombre: "One", 
                    imagen: "/logoPlaystation.png" 
                },
                {
                    consola: "PlayStations",
                    nombre: "Two", 
                    imagen: "/logoPlaystation.png" 
                },
                {
                    consola: "PlayStations",
                    nombre: "Three", 
                    imagen: "/logoPlaystation.png" 
                },
                {
                    consola: "Xbox",
                    nombre: "One", 
                    imagen: "/logoXbox.png" 
                },
                {
                    consola: "Xbox",
                    nombre: "Two", 
                    imagen: "/logoXbox.png" 
                },
                {
                    consola: "Xbox",
                    nombre: "Three", 
                    imagen: "/logoXbox.png" 
                },{
                    consola: "Nintendo",
                    nombre: "One", 
                    imagen: "/logoNintendo.png" 
                },
                {
                    consola: "Nintendo",
                    nombre: "Two", 
                    imagen: "/logoNintendo.png" 
                },
                {
                    consola: "Nintendo",
                    nombre: "Three", 
                    imagen: "/logoNintendo.png" 
                },
            ]
        }
    }, 
    methods: {
        showAlert(state, i){
            this.alertState[i] = state
        }, 
        showToast(state, i){
            this.toastState[i] = state
        }
    }
}
</script>


<style>

</style>