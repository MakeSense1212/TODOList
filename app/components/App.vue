<template>
    <Page>
        <ActionBar>
          <Button @tap="add" class="button">Ajouter une tâche</Button>

         <!-- <AbsoluteLayout v-if="true">
            <StackLayout>
              <Button>TEST</Button>
            </StackLayout>
          </AbsoluteLayout> -->
        </ActionBar>
      
        <ListView for="(item, index) in items" @itemTap="goToDetailsPage" height="100%" class="list" id="listview" name="listview">

          <v-template>
            <!-- Shows the list item label in the default color and style. -->
            <GridLayout columns="100, 2*" rows="100">
              <Image :src="item.get_image()" stretch="aspectFit" row="0" col="0"/>
              <!-- <Label :text="item.title" row="0" col="1" id="details-item-title"/> -->
              <Label :text="item.title" row="0" col="1" class="label"/>
          </GridLayout>
          </v-template>
        </ListView>

    </Page>
</template>

<script>
  import Vue from 'nativescript-vue';

  import ItemDetails from "~/components/ItemDetails";
  import Item from '~/models/Item';
  import {
      prompt,
      PromptResult,
      PromptOptions,
      inputType,
      capitalizationType
  } from "tns-core-modules/ui/dialogs"; 

  export default {
    components: {
      ItemDetails
    },
    data() {
      return {
        items: [
          new Item("1", "Anniversaire Maman", "Aller acheter un gateau d'anniversaire + trouver une idée de cadeau", "content", "category",  "Anniversaire Maman", "rating", "status"),
          new Item("2", "Aller au bar", "Sortir avec les potos", "content", "category",  "Bar", "rating", "status"),
          new Item("3", "Changer l'ampoule", "Changer la LED", "content", "category",  "Changer ampoule chambre", "rating", "status"),
          new Item("4", "Changer d'appartement", "Trouver un 60m² sur Nancy", "content", "category",  "Changerappartement", "rating", "status"),
          new Item("5", "Faire les courses", "Pain, beurre, farine, chocolat, ...", "content", "category",  "Course", "rating", "status"),
          new Item("6", "Devenir top500 sur overwatch", "Commencer à main BASTION pour gagner", "content", "category",  "Devenir TOP500 sur overwatch", "rating", "status"),
          new Item("7", "Faire du sport", "Placer mon premier dunk au basket", "content", "category",  "Faire du sport", "rating", "status"),
          new Item("8", "Faire mes devoirs", "Faire les projets du CESI à temps", "content", "category",  "Faire mes devoirs", "rating", "status"),
          new Item("9", "Faire mon lit", "Plier les draps", "content", "category",  "Faire mon lit", "rating", "status"),
          new Item("10", "Gagner la trackmania cup", "Apprendre à Néo-drift pour Bercy 2021", "content", "category",  "Gagner la TrachManiaCup", "rating", "status"),
          new Item("11", "Faire la lésive", "Lésive de couleur", "content", "category",  "Lésive", "rating", "status"),
          new Item("12", "Faire le menage", "Laver le salon", "content", "category",  "Menage", "rating", "status"),
          new Item("13", "Nourir le chat", "Meow!", "content", "category",  "Nourir le chat", "rating", "status"),
          new Item("14", "Finir mon projet mobile", "Pour vendredi 21/08 à 17h", "content", "category",  "Projet mobile", "rating", "status"),
          new Item("15", "Promener le chien", "Faire le tour du parc", "content", "category",  "Prommener le chien", "rating", "status"),
          new Item("16", "Faire la vaiselle", "Faire la vaiselle", "content", "category",  "Vaiselle", "rating", "status"),
        ]
      }
    },
    methods: {
      goToDetailsPage(args) {
        const item = args.item;
        this.$navigateTo(ItemDetails, { props: { item: item } });
      },
      add(){

        //this.items.push(new Item("17", "Faire la vaiselle", "Faire la vaiselle", "content", "category",  "Vaiselle", "rating", "status"));

        prompt({
          title: "Nouvelle tache",
          message: "Écrire le nom de la nouvelle tache:",
          okButtonText: "OK",
          cancelButtonText: "Annuler",
          defaultText: "",
        }).then(result => {
          console.log(`Dialog result: ${result.result}, text: ${result.text}`);
  
          let Nom = result.text;
          if(result.result)
          {
            prompt({
              title: "Description de la tache",
              message: "Décrire la tache:",
              okButtonText: "OK",
              cancelButtonText: "Annuler",
              defaultText: "",
            }).then(result => {
              console.log(`Dialog result: ${result.result}, text: ${result.text}`)
              let Description = result.text;
              if(result.result)
              this.items.push(new Item("17", Nom, Description, "content", "category",  "Vaiselle", "rating", "status"));
            });
          }
        });

        
        
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

   
    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    .pic {
    width: 60rem;
    }

    #layout {
      padding: 10px;
    }

    .label{
        white-space: normal;
    }
    
    .button{
      position: right;
      width: 300px;
      padding: 10px;
      background-color: #a03e3e49;
    }

    .list {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 35em;
    text-align: center;
    margin : 10em;
    display: flex;
    }
</style>
