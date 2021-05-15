<template>
  <v-container
    id="regular-tables"
    fluid
    tag="section"
  >
    <base-v-component
      heading="Simple Tables"
      link="components/simple-tables"
    />

    <base-material-card
      icon="mdi-clipboard-text"
      title="Simple Table"
      class="px-5 py-3"
    >
      <v-simple-table>
        <thead>
          <tr>
            <th class="primary--text">
              {{ tableHead.id }}
            </th>
            <th class="primary--text">
              {{ tableHead.name }}
            </th>
            <th class="primary--text">
              {{ tableHead.country }}
            </th>
            <th class="primary--text">
              {{ tableHead.city }}
            </th>
            <th class="text-right primary--text">
              {{ tableHead.salary }}
            </th>
          </tr>
        </thead>

        <tbody>
          <tr
            v-for="(rowData,i) in tableData"
            :key="i"
          >
            <td>{{ rowData.id }}</td>
            <td>{{ rowData.name }}</td>
            <td>{{ rowData.country }}</td>
            <td>{{ rowData.city }}</td>
            <td class="text-right">
              {{ rowData.salary }}
            </td>
          </tr>
        </tbody>
      </v-simple-table>
    </base-material-card>

    <div class="py-3" />

    <base-material-card
      color="success"
      dark
      icon="mdi-clipboard-plus"
      title="Table on Dark Background"
      class="px-5 py-3"
    >
      <v-data-table
        :headers="headers"
        :items="tableData"
        :items-per-page="6"
        class="elevation-1"
      />
    </base-material-card>
    <base-material-card
      color="warning"

      icon="mdi-clipboard-plus"
      title="Table on Dark Background"
      class="px-5 py-3"
    >
      <v-data-table
        :headers="headers"
        :items="tableData"
        :items-per-page="6"
        class="elevation-1"
      />
    </base-material-card>
  </v-container>
</template>
<script>
  export default {
    data () {
      return {
        tableHead: { id: 'ID', name: 'Name', country: 'Country', city: 'City', salary: 'Salary' },
        tableData: [
          { id: 1, name: 'Dakota Rice', country: 'Niger', city: 'Oud-Turnhout', salary: '$36,738' },
          { id: 2, name: 'Minverva Hooper', country: 'Curaçao', city: 'Sinaas-Waas', salary: '$23,789' },
          { id: 3, name: 'Sage Rodriguez', country: 'Netherlands', city: 'Baileux', salary: '$56,142' },
          { id: 4, name: 'Philip Chaney', country: 'Korea', city: 'South 서울', salary: '$38,735' },
          { id: 5, name: 'Doris Greene', country: 'Malawi', city: 'Feldkirchen in Kärnten', salary: '$63,542' },
          { id: 6, name: 'Mason Porter', country: 'Chile', city: 'Gloucester', salary: '$78,615' },
        ],
        headers: [
          {
            text: 'ID',
            align: 'start',
            sortable: false,
            value: 'id',
          },
          { text: 'Name', value: 'name' },
          { text: 'Country', value: 'country' },
          { text: 'City', value: 'city' },
          { text: 'Salary', value: 'salary' },
        ],

      }
    },

  }

</script>
