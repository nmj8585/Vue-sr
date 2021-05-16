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
      color="pink"
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
      color="deep-purple darken-4"
      cyan
      icon="mdi-clipboard-plus"
      title="이름가격도시연봉"
      class="px-5 py-3"
    >
      <v-data-table
        :hide-default-header="true"
        :hide-default-footer="false"
        :headers="headers"
        :items="tableData"
        :items-per-page="6"
        class="elevation-1"
      >
        <template v-slot:header="headObj">
          <tr>
            <th
              v-for="(head1,i) in headObj.props.headers"
              :key="i"
            >{{head1.text}}</th>
<!--            <th>{{ headObj.props.headers[0].text }}</th>-->
<!--            <th>{{ headObj.props.headers[1].text }}</th>-->
<!--            <th>{{ headObj.props.headers[2].text }}</th>-->
<!--            <th>{{ headObj.props.headers[3].text }}</th>-->
<!--            <th>{{ headObj.props.headers[4].text }}</th>-->
<!--            <th>삭제버튼</th>-->
          </tr>
        </template>
        <template v-slot:item="rowObj">
          <tr>
            <td>{{ rowObj.item.id }}</td>
            <td>{{ rowObj.item.name }}234</td>
            <td>{{ rowObj.item.fat }}</td>
            <td>{{ rowObj.item.protein }}</td>
            <td>{{ rowObj.item.iron }}</td>
            <td>
              <v-btn
                elevation="2"
              >
                삭제
              </v-btn>
            </td>
          </tr>
        </template>
      </v-data-table>
    </base-material-card>
  </v-container>
</template>
<script>
  export default {
    data () {
      return {
        tableHead: {
          id: 'ID',
          name: 'Name',
          country: 'Country',
          city: 'City',
          salary: 'Salary',
        },
        tableData: [
          {
            id: 1,
            name: 'Dakota Rice',
            country: 'Niger',
            city: 'Oud-Turnhout',
            salary: '$36,738',
          },
          {
            id: 2,
            name: 'Minverva Hooper',
            country: 'Curaçao',
            city: 'Sinaas-Waas',
            salary: '$23,789',
          },
          {
            id: 3,
            name: 'Sage Rodriguez',
            country: 'Netherlands',
            city: 'Baileux',
            salary: '$56,142',
          },
          {
            id: 4,
            name: 'Philip Chaney',
            country: 'Korea',
            city: 'South 서울',
            salary: '$38,735',
          },
          {
            id: 5,
            name: 'Doris Greene',
            country: 'Malawi',
            city: 'Feldkirchen in Kärnten',
            salary: '$63,542',
          },
          {
            id: 6,
            name: 'Mason Porter',
            country: 'Chile',
            city: 'Gloucester',
            salary: '$78,615',
          },
        ],
        headers: [
          {
            text: 'ID',
            align: 'start',
            sortable: false,
            value: 'id',
          },
          {
            text: 'Name',
            value: 'name',
          },
          {
            text: 'Country',
            value: 'country',
          },
          {
            text: 'City',
            value: 'city',
          },
          {
            text: 'Salary',
            value: 'salary',
          },
          {
            text: '삭제',
          },
        ],

      }
    },

  }

</script>
