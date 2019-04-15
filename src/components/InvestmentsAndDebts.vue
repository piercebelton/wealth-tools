<template>
  <v-container grid-list-lg id="investments-debts">
    <v-layout row>
      <v-flex xs12 class="text-xs-center display-1 font-weight-black my-5">Investments</v-flex>
    </v-layout>
<div>
  <v-dialog v-model="dialog" max-width="500px">
    <v-btn slot="activator" color="primary" dark class="mb-2">New Item</v-btn>
    <v-card>
      <v-card-title>
        <span class="headline">{{ formTitle }}</span>
      </v-card-title>
      <v-card-text>
        <v-container grid-list-md>
          <v-layout wrap>
            <v-flex xs12 sm6 md4>
              <v-text-field v-model="editedItem.name" label="Investment name"></v-text-field>
            </v-flex>
            <v-flex xs12 sm6 md4>
              <v-text-field v-model="editedItem.current_value" label="Current value"></v-text-field>
            </v-flex>
            <v-flex xs12 sm6 md4>
              <v-text-field v-model="editedItem.monthly_contribution" label="Monthly contribution"></v-text-field>
            </v-flex>
            <v-flex xs12 sm6 md4>
              <v-text-field v-model="editedItem.interest_rate" label="Interest rate"></v-text-field>
            </v-flex>
            <v-flex xs12 sm6 md4>
              <v-text-field v-model="editedItem.futureValue" label="Interest rate"></v-text-field>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue darken-1" flat @click.native="close">Cancel</v-btn>
        <v-btn color="blue darken-1" flat @click.native="save">Save</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
  <v-data-table :headers="headers" :items="investments" hide-actions class="elevation-1">
    <template slot="items" slot-scope="props">
      <td>{{ props.item.name }}</td>
      <td class="text-xs-right">{{ props.item.current_value }}</td>
      <td class="text-xs-right">{{ props.item.monthly_contribution }}</td>
      <td class="text-xs-right">{{ props.item.interest_rate }}</td>
      <td class="text-xs-right">{{ getFutureValue(props.item) }}</td>
      <td class="justify-center layout px-0">
        <v-btn icon class="mx-0" @click="editItem(props.item)">
          <v-icon color="teal">edit</v-icon>
        </v-btn>
        <v-btn icon class="mx-0" @click="deleteItem(props.item)">
          <v-icon color="pink">delete</v-icon>
        </v-btn>
      </td>
    </template>
  </v-data-table>
</div>
</v-container>
</template>


<script>

export default {
  name: 'InvestmentsAndDebts',
  data () {
    return {
      dialog: false,
      headers: [
        {
          text: 'Investment',
          align: 'left',
          sortable: false,
          value: 'name'
        },
        { text: 'Current value', value: 'current_value' },
        { text: 'Monthly contribution', value: 'monthly_contribution' },
        { text: 'Interest Rate', value: 'interest_rate' },
        { text: 'Actions', value: 'name', sortable: false }
      ],
      investments: [
        {
            name: 'Example Investment',
            current_value: 100000,
            monthly_contribution: 500,
            interest_rate: 1.9
          }
      ],
      editedIndex: -1,
      editedItem: {
        name: '',
        current_value: 0,
        monthly_contribution: 0,
        interest_rate: 0,
      },
      defaultItem: {
        name: '',
        current_value: 0,
        monthly_contribution: 0,
        interest_rate: 0,
      },
      listPrimitive: null
    }
  },
  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'New Item' : 'Edit Item'
    }
  },
  watch: {
    dialog(val) {
      val || this.close()
    }
  },
  methods: {
    editItem(item) {
      this.editedIndex = this.listPrimitive.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },
    deleteItem(item) {
      const index = this.listPrimitive.indexOf(item)
      confirm('Are you sure you want to delete this item?') && this.listPrimitive.delete(index)
    },
    close() {
      this.dialog = false
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      }, 300)
    },
    save() {
      if (this.editedIndex > -1) {
        this.investments.update(this.editedIndex, this.editedItem)
      } else {
        this.investments.push(this.editedItem)
      }
      this.close()
    },
    getFutureValue(item) {
      this.futureValue = item.current_value * 7;
      return this.futureValue;
    }
  }
};
</script>


<style scoped>
</style>
