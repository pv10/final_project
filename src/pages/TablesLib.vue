<template>
  <q-page>
    
    <q-toolbar class="bg-secondary text-black shadow-2">
      
      <q-tabs v-model="tab" shrink stretch>
        <q-tab name="saved" label="Saved" />
        <q-tab name="draft" label="Draft" />
      </q-tabs>

      <q-space />

      <q-btn flat label="+ Create Table" />
      <q-separator />
      <q-btn-dropdown color="primary" label="Sort">
      <q-list>
        <q-item clickable v-close-popup @click="onItemClick">
          <q-item-section>
            <q-item-label>Last Modified</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable v-close-popup @click="onItemClick">
          <q-item-section>
            <q-item-label>Alphabetically</q-item-label>
          </q-item-section>
        </q-item>

        
      </q-list>
    </q-btn-dropdown>



    </q-toolbar>
    <q-tab-panels v-model="tab" animated>
          <q-tab-panel name="saved">
            <div class="text-h6">Saved Tables</div>
            <div class="q-pa-md row items-start q-gutter-md">
              
              
              <div class="col-3" v-for=" item in TableData" :key="item.id">
                <q-card class="my-card">
                <!-- <img src="../assets/table-svgrepo-com.svg"> -->

                <q-card-section>
                  <div class="text-subtitle2">{{item.name}}</div>
                  <div class="text-subtitle2">{{item.date}}</div>
                </q-card-section>

                <q-card-section class="q-pt-none">
                  <!-- {{ lorem }} -->
                  <q-table
                    style="height: 100px"
                    flat bordered
                    :rows="rows"
                    :columns="columns"
                    row-key="index"
                    virtual-scroll
                    v-model:pagination="pagination"
                    :rows-per-page-options="[0]"
                  />

                </q-card-section>
              </q-card>
              </div>
            </div>
            
          </q-tab-panel>

          <q-tab-panel name="draft">
            <div class="text-h6">Tables in Draft</div>
            
          </q-tab-panel>
    </q-tab-panels>
      

</q-page>
</template>

<script>

import { ref } from 'vue'

const columns = [
  {
    name: 'index',
    label: '#',
    field: 'index'
  },
  {
    name: 'name',
    required: true,
    label: 'column',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'datatype', align: 'center', label: 'Calories', field: 'calories', sortable: true },
  { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true }

]

const seed = [
  {
    name: 'Frozen Yogurt',
    calories: 159,
    fat: 6.0,
    carbs: 24,
    protein: 4.0,
    sodium: 87,
    calcium: '14%',
    iron: '1%'
  }]

export default {
  // name: 'PageName',
  
  setup () {
    return {
      tab: ref('mails'),
      lorem: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
      TableData: [
        {name: 'table_01', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_02', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_03', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_04', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_05', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_06', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_07', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
        {name: 'table_08', date: '11-11-2023', colums: {col_name: 'id', dataType: 'int'}},
      
      ]
    }
      
  }
  
}

</script>

<style lang="sass" scoped>
.my-card
  width: 100%  
</style>
