<template>
  <q-page>
    <div class="row q-col-gutter-sm q-ma-xs q-mr-sm">
      <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12">
        <q-card flat bordered class square>
          <q-form @submit="onSubmit" ref="form">
            <q-card-section>
              <div class="text-h6">{{ schema.title }}</div>
            </q-card-section>
            <q-separator inset></q-separator>
            <q-card-section>
              <div class="row q-col-gutter-sm">
                <q-form-generator :schema="schema" :model="model"></q-form-generator>
              </div>
            </q-card-section>
            <q-card-actions align="right" class="q-pa-md">
              <q-btn label="Cancel" v-close-popup color="primary" flat></q-btn>
              <q-btn label="Submit" style="width: 100px" type="submit" color="primary" class="q-ml-sm"
                :loading="loading"></q-btn>
            </q-card-actions>
          </q-form>
        </q-card>
        <q-input v-model="textt" outlined dense square autogrow type="textarea"></q-input>
      </div>
      <div class="col-lg-8 col-md-8 col-sm-12 col-xs-12">
        <q-input v-model="text" outlined dense square autogrow type="textarea"></q-input>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  methods: {
    onSubmit() {

      console.log(this.model)
    }
  },
  computed: {
    textt: {
      get() {
        return JSON.stringify(this.model, null, 2)
      },
      set(val) {
        this.model = JSON.parse(val)
      },
    },
    text: {
      get() {
        return JSON.stringify(this.schema, null, 4)
      },
      set(val) {
        try {
          this.schema = JSON.parse(val)
        } catch (e) {
          // return console.error(e);
        }

      },
    },
  },

  data() {
    return {
      loading: false,
      required: (val) => (val && val.length > 0) || "This Field is Required",
      model: {
        // id: 1,
        name: '',
        password: 'J0hnD03!x4',
        skills: [],
        email: 'john.doe@gmail.com',
        date_of_birth: '',
        status: true
      },
      schema: {
        title: "Create a Form",
        position: "dialog",
        fields: [
          {
            type: "TextField",
            width: 12,
            mask: '',
            field: "name",
            label: "Name",
            required: true,
            readonly: false,
            disabled: false,
            sortable: true,
            align: 'left',
          },
          {
            type: "DateField",
            width: 6,
            field: "date_of_birth",
            label: "DOB",
            required: true,
            readonly: false,
            disabled: false,
            align: 'left',
          },
          {
            type: "TimeField",
            width: 6,
            mask: '',
            field: "start_time",
            label: "Start Time",
            required: true,
            readonly: false,
            disabled: false,
            sortable: true,
            align: 'left',
          },
          {
            type: "NumberField",
            width: 6,
            field: "age",
            label: "Age",
            required: true,
            readonly: false,
            disabled: false,
            sortable: true,
            align: 'left',
          },
          {
            type: "ColorPicker",
            width: 6,
            field: "color",
            label: "Color",
            required: true,
            readonly: false,
            disabled: false,
            sortable: true,
            align: 'left',
          },
          {
            type: "BarcodeScanner",
            width: 12,
            field: "barcode",
            label: "Barcode",
            required: true,
            readonly: false,
            disabled: false,
            sortable: true,
            align: 'left',
          },
          {
            type: "QRCodeScanner",
            width: 12,
            field: "qrcode",
            label: "QR Code",
            required: true,
            readonly: false,
            disabled: false,
            sortable: true,
            align: 'left',
          },
          {
            type: "Select",
            width: 12,
            label: "Skills",
            field: "skills",
            multiple: true,
            chips: false,
            required: true,
            sortable: true,
            align: 'left',
            options: ["HTML5", "Javascript", "CSS3", "CoffeeScript", "AngularJS", "ReactJS", "VueJS"]
          },
          {
            type: "Tree",
            width: 12,
            label: "Father",
            field: "father",
            required: true,
            multiple: true,
            sortable: true,
            align: 'left',
            options: [
              {
                id: 1, name: 'M khan',
                children: [
                  { id: 3, name: 'Saif' },
                  {
                    id: 4, name: 'Amaan',
                    children: [
                      { id: 6, name: 'Rehan' },
                      { id: 7, name: 'Farhan' }
                    ]
                  },
                ]
              },
              {
                id: 2, name: 'Shah khan',
                children: [
                  { id: 5, name: 'Usman' }
                ]
              },
            ]
          },

        ]
      },




    }
  }
}
</script>
