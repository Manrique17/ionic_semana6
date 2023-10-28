<template>
    <ion-page>
        <ion-header>
            
            <ion-toolbar>
                <ion-buttons>
                    <ion-back-button>Back</ion-back-button>
                </ion-buttons>
                <ion-title>Consolas</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
            <ion-grid>
                <ion-row>
                    <ion-col v-for="(consola, i) in consolas" :key="i">
                        <ion-card>
                            <img :src="consola.imagen" alt="">
                            <ion-card-header>
                                <ion-card-title>
                                    {{ consola.nombre }}
                                </ion-card-title>
                                <ion-card-subtitle>
                                    Juegos de {{ consola.nombre }}
                                </ion-card-subtitle>
                            </ion-card-header>
                            <ion-card-content>
                                {{ consola.descripcion }}
                            </ion-card-content>
                            <ion-button :href="`/tabs/juego/${consola.nombre}/${consola.id}`"
                                color="dark" size="small" expand="full">
                                Explorar juegos
                            </ion-button>
                        </ion-card>
                    </ion-col>
                </ion-row>
            </ion-grid>
        </ion-content>
    </ion-page>
        
    
</template>


<script>
import {IonPage, IonHeader, IonToolbar, IonContent, IonTitle, 
        IonGrid, IonRow, IonCol, IonCard, IonCardHeader, IonCardTitle, 
        IonCardSubtitle, IonCardContent, IonButton, IonButtons, IonBackButton } from '@ionic/vue';
export default{
    name: 'Inicio', 
    components: {
        IonPage, IonHeader, IonToolbar, IonContent, IonTitle, 
        IonGrid, IonRow, IonCol, IonCard, IonCardHeader, IonCardTitle, 
        IonCardSubtitle, IonCardContent, IonButton, IonButtons, IonBackButton
    }, 
    data(){
        return{
            consolas: [
                {id: 1, nombre: 'PlayStations', 
                descripcion: 'Juegos exclusivos para PlayStation', 
                imagen: '/logoPlaystation.png'}, 
                {id: 2, nombre: 'Xbox', 
                descripcion: 'Juegos exclusivos para XBox', 
                imagen: '/logoXbox.png'}, {id: 3, nombre: 'Nintendo', 
                descripcion: 'Juegos exclusivos para Nintendo', 
                imagen: '/logoNintendo.png'}, 
            ]
        }
    }
}
</script>


<style>

</style>