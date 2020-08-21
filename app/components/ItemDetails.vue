<template>
  <Page>
      <ActionBar title="Détails"/>
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
  }
};
</script>

<style>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .image{
           width: 100rem;
           margin-bottom: 50rem;
    }
    .label{
        white-space: normal;
    }

    .detail {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 30em;
    text-align: center;

    }
</style>