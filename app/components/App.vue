<template>
  <Page>
    <ActionBar title="Welcome to NativeScript-Vue!"/>
    <GridLayout columns="*" rows="*">
      <RadListView ref="listView"
                   row="0"
                   for="item in itemList"
                   pullToRefresh="true"
                   @pullToRefreshInitiated="onPullToRefreshInitiated">
        <v-template name="header">
          <StackLayout class="header">
            <Label text="Pull to refresh"></Label>
          </StackLayout>
        </v-template>

        <v-template>
          <StackLayout class="item" orientation="vertical">
            <Label :text="item.name">
            </Label>
          </StackLayout>
        </v-template>
      </RadListView>
    </GridLayout>
  </Page>
</template>

<script>
  import { fetch } from 'tns-core-modules/fetch'
  import { backendUrl } from '../constants'
  
  const getItems = () => {
    let headers = {
      'Accept': 'application/json',
      'Content-Type': 'application/json'
    }
    
    const payload = {
      headers,
      method: 'GET'
    }

    return new Promise((resolve, reject) => {
      console.log(`Getting items from ${backendUrl}...`)

      fetch(backendUrl, payload)
        .then((response) => {
          return response.json()
        })
        .then((data) => {
          resolve(data)
        })
      })
  };

  export default {
    data() {
      return {
        itemList: [
          {
            name: 'Apple',
          },
          {
            name: 'Orange',
          },
          {
            name: 'Tomato',
          }
        ],
      }
    },
    methods: {
      async onPullToRefreshInitiated ({ object }) {
        console.log('Pulling started. Getting items...');
        await this.fetchItems();
        console.log('Got items. Notifying that pull-to-refresh has finished...');
        object.notifyPullToRefreshFinished();
        console.log('Finished');
      },
      fetchItems () {
        return getItems()
          .then((data) => {
            this.itemList = data;
          })
        },
    },
  }
</script>

<style scoped>
  ActionBar {
    background-color: #53ba82;
    color: #ffffff;
  }
  .header {
    margin-bottom: 10px;
  }
</style>
