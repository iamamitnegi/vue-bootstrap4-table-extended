<template>
  <div id="app" class="container-fluid mb-10">
    <vue-bootstrap4-table
      :classes="classes"
      :sticky-header="stickyheader"
      :rows="rows"
      :footer="dfoot"
      :columns="columns"
      :config="config"
      :custom-filters="customFilters"
      @on-select-row="onSelectRows"
      @refresh-data="onRefreshData"
      :show-loader="showLoader"
      @on-download="onDownload"
    >
      <template slot="pagination-info" slot-scope="props">
        This page total is {{props.currentPageRowsLength}} |
        Filterd results total is {{props.filteredRowsLength}} |
        Original data total is {{props.originalRowsLength}}
      </template>

      <template slot="sort-asc-icon">
        <i class="fas fa-sort-up"></i>
      </template>
      <template slot="card-header">
        <div class="text-center">my title</div>
      </template>

      <template slot="global-search-clear-icon">
        <i class="fas fa-times-circle"></i>
      </template>
      <template slot="simple-filter-clear-icon">
        <i class="fas fa-times-circle"></i>
      </template>
      <template slot="paginataion-previous-button">Previous</template>
      <!-- <template slot="paginataion-next-button">
    <i class="fas fa-step-forward"></i>
      </template>-->

      <template slot="vbt-action-buttons">
        <div class="btn-group float-right" role="group" aria-label="Basic example">
          <button type="button" class="btn btn-secondary" @click="test">Left</button>
          <button type="button" class="btn btn-secondary">Middle</button>
          <button type="button" class="btn btn-secondary">Right</button>
        </div>
      </template>
      <template slot="sort-desc-icon">
        <i class="fas fa-sort-down"></i>
      </template>
      <template slot="no-sort-icon">
        <i class="fas fa-sort"></i>
      </template>

      <template slot="refresh-button-text">
        <font-awesome-icon icon="user-secret" />my refresh
      </template>

      <template slot="action-btn-download-icon">
        <font-awesome-icon icon="user-secret" />test
      </template>

      <template slot="reset-button-text">⟳ my reset</template>
      <template slot="empty-results">your custom message</template>
      <template slot="lastname-filter" slot-scope="props">
        <input
          type="text"
          class="form-control"
          placeholder="Enter lastname"
          @keyup.stop="updateLastNamefilter($event)"
        />
      </template>
    </vue-bootstrap4-table>
  </div>
</template>

<script>
import VueBootstrap4Table from "./components/VueBootstrap4Table.vue";

var chance = require("chance").Chance(88);
export default {
  name: "App",
  data: function() {
    return {
      therapist: [
        {
          dateRange: "current",
          "07F6478853F14146938F799A09BF6551": "0.00",
          "41D710A3D72D4836A4C8A23DB1D33AC9": "0.00",
          "5022EE63495641ED9362A4E88326B5B4": "0.00",
          "73BD0D50C3624BAA909A320B05996394": "0.00",
          "8060A39F60E841B3989A88077B10EF21": "0.00",
          "763FD4252CC147878D1B2D1136E87749": "50.00",
          FE153A69D8CE447BB6E0EA8B9B6DC49D: "0.00",
          F8CA857F8FDB4240AB524D260358BF6A: "0.00",
          "7F696E29E9F24E91AF357459945F5FD6": "0.00",
          D12439D8EA254757BD2FC5D034D9AE73: "0.00"
        },
        {
          dateRange: "31-60",
          "07F6478853F14146938F799A09BF6551": "0.00",
          "41D710A3D72D4836A4C8A23DB1D33AC9": "190.00",
          "5022EE63495641ED9362A4E88326B5B4": "0.00",
          "73BD0D50C3624BAA909A320B05996394": "0.00",
          "8060A39F60E841B3989A88077B10EF21": "0.00",
          "763FD4252CC147878D1B2D1136E87749": "0.00",
          FE153A69D8CE447BB6E0EA8B9B6DC49D: "0.00",
          F8CA857F8FDB4240AB524D260358BF6A: "0.00",
          "7F696E29E9F24E91AF357459945F5FD6": "410.00",
          D12439D8EA254757BD2FC5D034D9AE73: "10.00"
        },
        {
          dateRange: "61-90",
          "07F6478853F14146938F799A09BF6551": "0.00",
          "41D710A3D72D4836A4C8A23DB1D33AC9": "0.00",
          "5022EE63495641ED9362A4E88326B5B4": "0.00",
          "73BD0D50C3624BAA909A320B05996394": "600.00",
          "8060A39F60E841B3989A88077B10EF21": "720.00",
          "763FD4252CC147878D1B2D1136E87749": "0.00",
          FE153A69D8CE447BB6E0EA8B9B6DC49D: "0.00",
          F8CA857F8FDB4240AB524D260358BF6A: "0.00",
          "7F696E29E9F24E91AF357459945F5FD6": "0.00",
          D12439D8EA254757BD2FC5D034D9AE73: "0.00"
        },
        {
          dateRange: "91-120",
          "07F6478853F14146938F799A09BF6551": "0.00",
          "41D710A3D72D4836A4C8A23DB1D33AC9": "10.00",
          "5022EE63495641ED9362A4E88326B5B4": "0.00",
          "73BD0D50C3624BAA909A320B05996394": "0.00",
          "8060A39F60E841B3989A88077B10EF21": "0.00",
          "763FD4252CC147878D1B2D1136E87749": "0.00",
          FE153A69D8CE447BB6E0EA8B9B6DC49D: "600.00",
          F8CA857F8FDB4240AB524D260358BF6A: "480.00",
          "7F696E29E9F24E91AF357459945F5FD6": "0.00",
          D12439D8EA254757BD2FC5D034D9AE73: "0.00"
        },
        {
          dateRange: "121+",
          "07F6478853F14146938F799A09BF6551": "80.00",
          "41D710A3D72D4836A4C8A23DB1D33AC9": "0.00",
          "5022EE63495641ED9362A4E88326B5B4": "50.00",
          "73BD0D50C3624BAA909A320B05996394": "0.00",
          "8060A39F60E841B3989A88077B10EF21": "0.00",
          "763FD4252CC147878D1B2D1136E87749": "0.00",
          FE153A69D8CE447BB6E0EA8B9B6DC49D: "0.00",
          F8CA857F8FDB4240AB524D260358BF6A: "0.00",
          "7F696E29E9F24E91AF357459945F5FD6": "0.00",
          D12439D8EA254757BD2FC5D034D9AE73: "0.00"
        },
        {
          dateRange: "total",
          "07F6478853F14146938F799A09BF6551": "80.00",
          "41D710A3D72D4836A4C8A23DB1D33AC9": "200.00",
          "5022EE63495641ED9362A4E88326B5B4": "50.00",
          "73BD0D50C3624BAA909A320B05996394": "600.00",
          "8060A39F60E841B3989A88077B10EF21": "720.00",
          "763FD4252CC147878D1B2D1136E87749": "50.00",
          FE153A69D8CE447BB6E0EA8B9B6DC49D: "600.00",
          F8CA857F8FDB4240AB524D260358BF6A: "480.00",
          "7F696E29E9F24E91AF357459945F5FD6": "410.00",
          D12439D8EA254757BD2FC5D034D9AE73: "10.00"
        }
      ],
      therapistList: {
        "07F6478853F14146938F799A09BF6551": "Hagrid, Rubeus",
        "41D710A3D72D4836A4C8A23DB1D33AC9": "Hunter, Jo",
        "5022EE63495641ED9362A4E88326B5B4": "Knight, Lillian",
        "73BD0D50C3624BAA909A320B05996394": "Lestrange, Bellatrix",
        "8060A39F60E841B3989A88077B10EF21": "Malfoy, Draco",
        "763FD4252CC147878D1B2D1136E87749": "Potter, Harry",
        FE153A69D8CE447BB6E0EA8B9B6DC49D: "Riddle, Tom",
        F8CA857F8FDB4240AB524D260358BF6A: "Shrivastav, Vaibhav",
        "7F696E29E9F24E91AF357459945F5FD6": "Something, Joe",
        D12439D8EA254757BD2FC5D034D9AE73: "Thompson, Cory"
      },
      rows: [],
      customFilters: [],
      total_rows: 0,
      stickyheader: true,
      showLoader: false,
      list: [
        {
          name: "Irwin",
          value: "Irwin"
        },
        {
          name: "Don",
          value: "Don"
        },
        {
          name: "Bessie",
          value: "Bessie"
        }
      ],
      columns: [
        {
          label: "Name",
          name: "name",
          row_text_alignment: "text-left",
          sort: true
        },
        {
          label: "Current",
          name: "current",
          row_text_alignment: "text-right"
        },
        {
          label: "31-60 DAYS",
          name: "31-60",
          row_text_alignment: "text-right"
        },
        {
          label: "61-90 DAYS",
          name: "61-90",
          row_text_alignment: "text-right"
        },
        {
          label: "91-120 DAYS",
          name: "91-120",
          row_text_alignment: "text-right"
        },
        {
          label: "121+ DAYS",
          name: "121+",
          row_text_alignment: "text-right"
        },
        {
          label: "Total",
          name: "total",
          row_text_alignment: "text-right",
          sort: true
        }
      ],
      dfoot: [" ", "$200", "$300", "$400", "$500", "$600", "$700"],

      config: {
        pagination: false, // default true
        show_refresh_button: false,
        show_reset_button: false,
        pagination_info: false, // default true
        card_title: "Account Balance - Table View",
        global_search: {
          placeholder: "Search by name",
          visibility: true,
          case_sensitive: false,
          showClearButton: true,
          searchOnPressEnter: false,
          searchDebounceRate: 1000
        }
      },
      classes: {
        // tableWrapper: "",
        table: {
          "table-striped my-class": true,
          "table-bordered my-class-two": function(rows) {
            return true;
          }
        },
        row: {
          "my-row my-row2": true,
          "function-class": function(row) {
            return row.id == 1;
          }
        },
        cell: {
          "my-cell my-cell2": true,
          "text-danger": function(row, column, cellValue) {
            return column.name == "salary" && row.salary > 2500;
          }
        }
        // table : "table-striped table-bordered my-class",
      },
      // actions: []
      actions: [
        {
          // btn_text: '<font-awesome-icon icon="user-secret" />',
          btn_text_slot_name: "action-btn-download-icon",
          class: "btn btn-primary",
          event_name: "on-download",
          event_payload: {
            msg: "my custom msg"
          }
        },
        {
          btn_text: '<span> <i class="fas fa-download"></i> Download</span>',
          class: "btn-info",
          event_name: "on-download",
          event_payload: {
            msg: "my custom msg"
          }
        }
      ],
      startDate: "2017-09-05",
      endDate: "2017-09-15",
      locale: {
        direction: "ltr", //direction of text
        format: "DD-MM-YYYY", //fomart of the dates displayed
        separator: " - ", //separator between the two ranges
        applyLabel: "Apply",
        cancelLabel: "Cancel",
        weekLabel: "W",
        customRangeLabel: "Custom Range"
      }
    };
  },
  methods: {
    updateEmailfilter(event) {
      let index = this.customFilters.findIndex(
        customFilter => customFilter.name === "email"
      );
      if (index == -1) {
        this.customFilters.push({
          name: "email",
          text: event.target.value,
          type: "custom"
        });
      } else {
        this.customFilters[index].text = event.target.value;
      }
    },
    updateLastNamefilter(event) {
      let index = this.customFilters.findIndex(
        customFilter => customFilter.name === "name.last_name"
      );
      if (index == -1) {
        this.customFilters.push({
          name: "name.last_name",
          text: event.target.value,
          type: "custom"
        });
      } else {
        this.customFilters[index].text = event.target.value;
      }
    },
    formatTableData() {
      let clients = this.therapist;
      let clientsID = Object.keys(this.therapistList);
      for (var x = 0; x < clientsID.length; x++) {
        let obj = {
          name: null,
          id: null,
          current: null,
          "31-60": null,
          "61-90": null,
          "91-120": null,
          "121+": null,
          total: null
        };
        let getID = clientsID[x];
        obj["name"] = this.therapistList[getID];
        obj["id"] = getID;

        // add row
        for (let i = 0; i < clients.length; i++) {
          let getDaterange = clients[i]["dateRange"];
          obj[getDaterange] = clients[i][getID];
        }
        this.rows.push(obj);
      }
      console.log("this is rows data", this.rows);
    },
    // fetchData() {
    //   let user;
    //   let users = [];
    //   for (let i = 1; i <= 100; i++) {
    //     user = {
    //       id: i,
    //       name: {
    //         first_name: chance.first(),
    //         last_name: chance.last()
    //       },
    //       age: chance.age(),
    //       address: {
    //         city: chance.city(),
    //         street: chance.address(),
    //         postcode: chance.postcode(),
    //         country: chance.country({ full: true })
    //       },
    //       salary: chance.integer({ min: 1500, max: 3000 }),
    //       email: [{ value: chance.email() }],
    //       website: chance.domain(),
    //       mobile: chance.phone()
    //     };
    //     users.push(user);
    //   }
    //   user = {
    //     id: 103,
    //     name: {
    //       first_name: null,
    //       last_name: null
    //     },
    //     age: chance.age(),
    //     address: {
    //       city: chance.city(),
    //       street: chance.address(),
    //       postcode: chance.postcode(),
    //       country: chance.country({ full: true })
    //     },
    //     salary: chance.integer({ min: 1500, max: 3000 }),
    //     email: [{ value: chance.email() }],
    //     website: chance.domain(),
    //     mobile: chance.phone()
    //   };
    //   users.push(user);

    //   user = {
    //     id: 104,
    //     name: {
    //       first_name: "voll",
    //       last_name: chance.last()
    //     },
    //     age: chance.age(),
    //     address: {
    //       city: chance.city(),
    //       street: chance.address(),
    //       postcode: chance.postcode(),
    //       country: chance.country({ full: true })
    //     },
    //     salary: chance.integer({ min: 1500, max: 3000 }),
    //     email: [{ value: chance.email() }],
    //     website: chance.domain(),
    //     mobile: chance.phone()
    //   };
    //   users.push(user);

    //   this.rows = users;
    // },
    onSelectRows(payload) {
      console.log(payload);
    },
    onDownload(payload) {
      console.log(payload);
    },
    test() {
      alert(33);
    },
    onRefreshData() {
      let dummy = [
        {
          name: {
            first_name: "asdf",
            last_name: "afds"
          },
          id: 1,
          age: 27,
          address: {
            city: "Port asdf",
            street: "311 Marlen Skyway Suite 457",
            postcode: "59419",
            country: "Mayotte"
          },
          salary: 2574,
          email: "franecki.asfd@gmail.com",
          website: "reichert.info",
          mobile: "+1-704-796-2565"
        },
        {
          name: {
            first_name: "xcv",
            last_name: "asdf"
          },
          id: 2,
          age: 23,
          address: {
            city: "asdf",
            street: "asdf Tiara Valleys",
            postcode: "df-4010",
            country: "sdfa"
          },
          salary: 2126,
          email: "rlittle@macejkovic.biz",
          website: "wisoky.com",
          mobile: "+asf"
        },
        {
          name: {
            first_name: "asdfsdf",
            last_name: "asdf"
          },
          id: 3,
          age: 30,
          address: {
            city: "asf",
            street: "7729 Ashleigh Radial Apt. 649",
            postcode: "54914-6608",
            country: "Papua New Guinea"
          },
          salary: 3805,
          email: "delasfia.becker@cormier.com",
          website: "ksdfuhlman.com",
          mobile: "220.872.2938 x35208"
        }
      ];
      this.formatTableData();
      // this.$nextTick(() => {
      //     this.config.page= 4;
      // });
      // this.rows = dummy;
    }
  },
  components: {
    VueBootstrap4Table
  },
  mounted() {
    let self = this;
    this.formatTableData();
    this.columns[1].filter.options = this.list;
    // let test = [1,2,3,4,5,6,7]

    // test.some((val,index) => {
    //     console.log(val);
    //     if (val == 3) {
    //         return true
    //     }

    // })
  }
};
</script>

<style>
.vbt-row-selected {
  background-color: rgb(131, 102, 102) !important;
}

.my-margin {
  margin: 10px;
}
</style>
