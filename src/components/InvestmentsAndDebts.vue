<template>
    <v-container grid-list-lg id="investments-debts">
        <v-layout row>
            <v-flex xs12 class="text-xs-center display-1 font-weight-black my-5">Available Tools</v-flex>
        </v-layout>

        <v-layout row wrap>
            <v-flex>
                <v-card height="500px">
                    <v-card-title primary-title>
                        <v-flex xs12 s3 md3 lg3>
                          <h3 class="headline mb-0">Investment</h3><br>
                            <div>
                                <h4>Enter Details Below</h4>
                                <v-text-field id="balance" label="Current Balance" />
                                <v-text-field id="monthly-plus" label="Monthly Contribution" />
                                <v-text-field id="interest" label="Interest Rate" />
                            </div>
                        </v-flex>
                        <v-flex xs12 s9 md9 lg9>
                            <div id="tbl"><br><br>
                                <h4>Future Estimated Value:</h4>
                                <v-data-table
                                  :headers="headers"
                                  :items="investments"
                                  class="elevation-1">
                                  <template v-slot:items="props">
                                    <td>{{ props.item.name }}</td>
                                    <td class="text-xs-left">{{ props.item.value }}</td>
                                  </template>
                                </v-data-table>
                            </div>
                        </v-flex>
                    </v-card-title>
                </v-card>
            </v-flex>
        </v-layout>

        <v-layout row wrap>
            <v-flex>
                <v-card height="500px">
                    <v-card-title primary-title>
                        <div>
                            <h3 class="headline mb-0">Debt</h3>
                            <v-text-field label="Label e.g. 'Mortgage'" />
                            <v-text-field label="Principle" />
                            <v-text-field label="Interest Rate" />
                        </div>
                    </v-card-title>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    name: 'InvestmentsAndDebts',
    data () {
      return {
        headers: [
          {
            text: 'Investment',
            align: 'left',
            sortable: false,
            value: 'name'
          },
          { text: 'Value', value: 'value' }
        ],
        investments: [
          {
            name: 'Apartments',
            value: 10000
          }
        ]
      }
    }
};
</script>


<style scoped>
</style>
