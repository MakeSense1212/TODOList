<template>
  <Page>
      <ActionBar title="Détails">
        <Button @tap="edit" class="button">modifier</Button>
      </ActionBar>
      <StackLayout class="detail">
          <Image :src="item.get_image()" stretch="aspectFit" class="image"/>
          <Label :text="item.description" class="label"/>
      </StackLayout>
  </Page>
</template>

<script>
import Item from "../models/Item";

export default {
  name: "ItemDetails",
  props: {
    item: Item,
  },

   methods: {
    edit(){
      prompt({
          title: "Modifier le nom de la tache",
          message: "Saisir le nouveau nom de la tache:",
          okButtonText: "OK",
          cancelButtonText: "Annuler",
          defaultText: this.item.title,
        }).then(result => {
          console.log(`Dialog result: ${result.result}, text: ${result.text}`);

          let Nom = result.text;
          if(result.result)
          {
            prompt({
              title: "Modifier la description de la tache",
              message: "Décrire la tache:",
              okButtonText: "OK",
              cancelButtonText: "Annuler",
              defaultText: this.item.description,
            }).then(result => {
              console.log(`Dialog result: ${result.result}, text: ${result.text}`)
              let Description = result.text;
              if(result.result){
              this.item.title = Nom;
              this.item.description = Description;
              }
            });
          }
      });
    },
    erase(){
     
    }
  }
};
</script>

<style>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .image{
          margin-top: 60px;
           width: 100rem;
           margin-bottom: 50rem;
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

    .detail {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 30em;
    text-align: center;

    }
</style>