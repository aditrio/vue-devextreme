<template>
  <div class="content-block">
    <h2>Test</h2>
    <div class="dx-card responsive-paddings">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Unde dolor
        repellendus veniam quos! Illo obcaecati amet quo cumque dolore quis quas
        nemo, minima, pariatur molestias deleniti, placeat aspernatur! Aliquid,
        neque.
      </p>
      <br />
      <DxDataGrid
        id="dataGrid"
        :data-source="data"
        key-expr="id"
        allow-column-reordering="true"
        loadPanel="true "
      >
        <!-- settings -->
        <DxEditing
          :allow-adding="true"
          :allow-updating="true"
          :allow-deleting="true"
          mode="popup"
        />
        <DxForm label-location="top" />
        <DxPopup :show-title="true" title="Data" />
        <DxSelection mode="multiple" />
        <DxFilterRow :visible="false" />
        <DxSearchPanel :visible="true" />
        <DxHeaderFilter :visible="true" />
        <DxGrouping :context-menu-enabled="true" />
        <DxGroupPanel :visible="true" />
        <DxPaging :page-size="5" :page-index="1" />

        <!-- column -->
        <DxColumn
          :width="200"
          :allow-sorting="false"
          data-field="gambar"
          cell-template="pict"
        />
        <DxColumn :allow-header-filtering="false" data-field="kode"></DxColumn>
        <DxColumn data-field="nama"></DxColumn>

        <DxColumn data-field="harga" />
        <DxColumn data-field="is_ready"></DxColumn>

        <!-- template -->
        <template #pict="{ data }">
          <img class="thumbnail" :src="'./img/' + data.value" />
        </template>
      </DxDataGrid>
    </div>
  </div>
</template>

<script>
import "devextreme/dist/css/dx.common.css";
import "devextreme/dist/css/dx.light.css";
// import axios from "axios";
// import service from "../services/employees.service";
import data from "../services/test.service";

import {
  DxDataGrid,
  DxColumn,
  DxFilterRow,
  DxSearchPanel,
  DxHeaderFilter,
  DxPaging,
  DxGrouping,
  DxGroupPanel,
  DxSelection,
  DxEditing,
  DxForm,
  DxPopup,
} from "devextreme-vue/data-grid";

export default {
  name: "Test",
  components: {
    DxDataGrid,
    DxColumn,
    DxFilterRow,
    DxSearchPanel,
    DxHeaderFilter,
    DxPaging,
    DxGrouping,
    DxGroupPanel,
    DxSelection,
    DxEditing,
    DxForm,
    DxPopup,
  },
  data() {
    return {
      data: {},
    };
  },
  methods: {
    bindData(Data) {
      this.data = Data;
    },
  },
  mounted() {
    this.bindData(data.getData());
  },
};
</script>

<style>
.thumbnail {
  object-fit: cover;
  height: 100px;
}
</style>