<!-- eslint-disable vue/no-template-shadow -->
<template>
    <div class="container mt-5">
        <div class="blue-grey lighten-3 text-left">
            <h3 class="ms-3 pt-3 pb-3">PIPING</h3>
        </div>
        <v-card
            class="ps-10 pe-10 pt-5 pb-10"
            outlined
            tile
        >
        <div align="right" class="mb-5">
            <v-btn
                elevation="2"
                color="text-h8 dark lighten-2 pa-2"
                @click="(dialogIAdd = true),cleardatapup()"
            ><span class="mdi mdi-plus" style="font-size: 20px;"></span><span>Add Piping</span>
            </v-btn>
        </div>
            <div>
                <v-simple-table
                    fixed-header
                    height="600px"
                >                    
                    <thead>
                        <tr>
                        <th class="text-left">
                            No.
                        </th>
                        <th class="text-left">
                            Line number
                        </th>
                        <th class="text-left">
                            location
                        </th>
                        <th class="text-left">
                            from
                        </th>
                        <th class="text-left">
                            to
                        </th>
                        <th class="text-left">
                            Pipe size (inch)
                        </th>
                        <th class="text-left">
                            Service
                        </th>
                        <th class="text-left">
                            Material
                        </th>
                        <th></th>
                        </tr>
                    </thead>
                    <tbody class="">
                        <tr
                        v-for="(item,index) in desserts" :key="index">
                        <td>{{ index+1 }}</td>
                        <td>{{ item.line_number}}</td>
                        <td>{{ item.location }}</td>
                        <td>{{ item.from }}</td>
                        <td>{{ item.to }}</td>
                        <td>{{ item.pipe_size }}</td>
                        <td>{{ item.service }}</td>
                        <td>{{ item.material }}</td>
                        <td>
                            <v-btn
                            color="primary"
                            x-small
                            @click="
                                selectedItem = item;
                                Senddatapup(item);
                                dialogI = true;
                            ">
                            <span class="mdi mdi-information-outline" style="font-size: 15px;"></span><span>Info</span>
                            </v-btn>

                            <v-btn
                            color="primary"
                            x-small
                            @click="
                                selectedItem = item;
                                btn1(selectedItem);                               
                            ">
                            <span class="mdi mdi-details" style="font-size: 15px;"></span><span>Detail</span>
                            </v-btn>
                        </td>
                        </tr>
                    </tbody>                    
                </v-simple-table>               
            </div>
        </v-card>
        
        <!-- Popup INFO -->
        <div class="text-center">
            <v-dialog
            v-model="dialogI"
            width="900"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                PIPING INFORMATION
                </v-card-title>
                <v-card-text>
                    <v-form>
                    <v-container>
                    <v-row>
                        <v-col
                        cols="12"
                        sm="6"
                        >
                        <v-text-field
                                v-model="line_number"
                                label="Line number"
                            ></v-text-field>
                            <v-text-field
                                v-model="from"
                                label="From"
                            ></v-text-field>
                            <v-text-field
                                v-model="drawing_number"
                                label="Drawing number"
                            ></v-text-field>
                            <v-text-field
                                v-model="material"
                                label="Material"
                            ></v-text-field>
                            <div style="display: flex; align-items: center;">
                                <v-select v-model="pipe_size" :items="items" label="Pipe size"></v-select>
                                <v-btn class="mx-2" x-small fab dark color="indigo" @click="dialogpipe = true">
                                    <v-icon dark>
                                        mdi-plus
                                    </v-icon>
                                </v-btn> 
                            </div>
                            <v-text-field
                                v-model="stress"
                                label="Stress"
                            ></v-text-field>
                            <v-text-field
                                v-model="ca"
                                label="ca"
                            ></v-text-field>
                            <v-text-field
                                v-model="design_pressure"
                                label="design pressure"
                            ></v-text-field>
                            <v-text-field
                                v-model="design_temperature"
                                label="design temperature"
                            ></v-text-field>
                            <!-- <v-text-field
                                :value = "selectedItem.line_number"
                                label="Line number"
                            ></v-text-field> -->
                        </v-col>

                        <v-col
                            cols="12"
                            sm="6"
                            >
                            <v-text-field
                                v-model="location"
                                label="Location"
                            ></v-text-field> 
                            <v-text-field
                                v-model="to"
                                label="To"
                            ></v-text-field>
                            <v-text-field
                                v-model="service"
                                label="Service"
                            ></v-text-field>
                            <v-text-field
                                v-model="inservice_date"
                                label="Inservice date"
                            ></v-text-field>
                            <v-text-field
                                v-model="original_thickness"
                                label="Original thickness"
                            ></v-text-field>
                            <v-text-field
                                v-model="joint_efficiency"
                                label="Joint effciency"
                            ></v-text-field>
                            <v-text-field
                                v-model=" design_life"    
                                label="design life"                                
                            ></v-text-field>
                            <v-text-field
                                v-model="operating_pressure"
                                label="operating pressure"                                
                            ></v-text-field>
                            <v-text-field
                                v-model="operating_temperature"
                                label="operating temperature"                                
                            ></v-text-field>    
                        </v-col>
                    </v-row>
                    </v-container>
                </v-form>
                
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions>
                <v-spacer></v-spacer>

                <v-btn
                    color="success"
                    text
                    @click="dialogsave = true"
                >
                <span class="mdi mdi-content-save-edit-outline"></span>Save
                </v-btn>
                <v-btn
                    color="red"
                    text
                    @click="(dialogdel = true)"
                >
                <span class="mdi mdi-delete-alert-outline"></span>Delete
                </v-btn>
                <v-btn
                    color="Dark"
                    text
                    @click="dialogI = false"
                >                    
                <span class="mdi mdi-close-circle-outline"></span>Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

         <!-- Popup INFOADD -->
         <div class="text-center">
            <v-dialog
            v-model="dialogIAdd"
            width="900"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                PIPING INFORMATION ADD
                </v-card-title>
                
                <v-card-text>
                    <v-form>
                    <v-container>
                    <v-row>
                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="line_number"
                                label="Line number"
                            ></v-text-field>
                            <v-text-field
                                v-model="from"
                                label="From"
                            ></v-text-field>
                            <v-text-field
                                v-model="drawing_number"
                                label="Drawing number"
                            ></v-text-field>
                            <v-text-field
                                v-model="material"
                                label="Material"
                            ></v-text-field>
                            <div style="display: flex; align-items: center;">
                                <v-select v-model="pipe_size" :items="items" label="Pipe size"></v-select>
                                <v-btn class="mx-2" x-small fab dark color="indigo" @click="dialogpipe = true">
                                    <v-icon dark>
                                        mdi-plus
                                    </v-icon>
                                </v-btn> 
                            </div>
                            <v-text-field
                                v-model="stress"
                                label="Stress"
                            ></v-text-field>
                            <v-text-field
                                v-model="ca"
                                label="ca"
                            ></v-text-field>
                            <v-text-field
                                v-model="design_pressure"
                                label="design pressure"
                            ></v-text-field>
                            <v-text-field
                                v-model="design_temperature"
                                label="design temperature"
                            ></v-text-field>
                        </v-col>


                        <v-col
                            cols="12"
                            sm="6"
                            >
                            <v-text-field
                                v-model="location"
                                label="Location"
                            ></v-text-field> 
                            <v-text-field
                                v-model="to"
                                label="To"
                            ></v-text-field>
                            <v-text-field
                                v-model="service"
                                label="Service"
                            ></v-text-field>
                            <v-text-field
                                v-model="inservice_date"
                                label="Inservice date"
                            ></v-text-field>
                            <v-text-field
                                v-model="original_thickness"
                                label="Original thickness"
                            ></v-text-field>
                            <v-text-field
                                v-model="joint_efficiency"
                                label="Joint effciency"
                            ></v-text-field>
                            <v-text-field
                                v-model=" design_life"    
                                label="design life"                                
                            ></v-text-field>
                            <v-text-field
                                v-model="operating_pressure"
                                label="operating pressure"                                
                            ></v-text-field>
                            <v-text-field
                                v-model="operating_temperature"
                                label="operating temperature"                                
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    </v-container>
                </v-form>
                
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions>
                <v-spacer></v-spacer>

                <v-btn
                    color="success"
                    text
                    @click="SaveData()"
                >
                <span class="mdi mdi-content-save-edit-outline"></span>Save
                </v-btn>
                <v-btn
                    color="red"
                    text
                    @click="dialogIAdd = false"
                >
                <span class="mdi mdi-close-circle-outline"></span>Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup confirmdel -->
        <v-row justify="center">
            <v-dialog
            v-model="dialogdel"
            persistent
            max-width="290"
            >
            <v-card>
                <v-card-title class="text-h5">
                Confirm Delete?
                </v-card-title>
                <v-card-text>ยืนยันการลบข้อมูลออก</v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="red darken-1"
                    text
                    @click="dialogdel = false,dialogI = false,Deletedata(selectedItem)"
                >
                <span class="mdi mdi-delete-alert-outline"></span>Delete
                </v-btn>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogdel = false"
                >
                <span class="mdi mdi-close-circle-outline"></span>Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-row>

        <!-- Popup confirmsave -->
        <v-row justify="center">
            <v-dialog
            v-model="dialogsave"
            persistent
            max-width="290"
            >
            <v-card>
                <v-card-title class="text-h5">
                Confirm Save?
                </v-card-title>
                <v-card-text>ยืนยันการแก้ไขข้อมูล</v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="success"
                    text
                    @click="dialogsave = false,dialogI = false,Saveeditdata(selectedItem)"
                >
                <span class="mdi mdi-content-save-edit-outline"></span>Save
                </v-btn>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogsave = false"
                >
                <span class="mdi mdi-close-circle-outline"></span>Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-row>

        <!-- Popup pipe -->
        <v-row justify="center">
            <v-dialog
            v-model="dialogpipe"
            persistent
            max-width="290"
            >
            <v-card>
                <v-card-title class="text-h5">
                Add pipe size?
                </v-card-title>
                <v-card-text>
                    ต้องการเพิ่มขนาดท่อ ?
                    <br>(หากท่านต้องการลบให้ระบุ Pipe size)
                    <v-text-field
                        v-model="pipe_sizeadd"
                        label="Pipe size"
                    ></v-text-field>
                    <v-text-field
                        v-model="Actual_outside_diameter"
                        label="Actual outside diameter"
                    ></v-text-field>    

                </v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="success"
                    text
                    @click="dialogpipe = false,addpipesize(),clearpipesize()"
                >
                <span class="mdi mdi-plus"></span>ADD
                </v-btn>
                <v-btn
                    color="red"
                    text
                    @click="dialogpipe = false,delpipsize(),clearpipesize()"
                >
                <span class="mdi mdi-delete-alert-outline"></span>Delete
                </v-btn>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogpipe = false,clearpipesize()"
                >
                <span class="mdi mdi-close-circle-outline"></span>Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-row>        

    </div>
</template>    


<script>
export default {
  data () {
    return {
        selectedItem : [],
        item : null,
        dialogI : false,
        dialogpipe : false,
        dialogIAdd : false,
        dialogdel : false,
        dialogsave : false,
        dialogAddcml : false,
        desserts: [],
        dessertsdetail: [],
        items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
        pipe_sizeadd:'',
        Actual_outside_diameter:'',

        line_number:'',
        location:'',
        from:'',
        to:'',
        drawing_number:'',
        service:'',
        material:'',
        inservice_date:'',
        pipe_size:'',
        original_thickness:'',
        stress:'',
        joint_efficiency:'',
        ca:'',
        design_pressure:'',
        operating_pressure:'',
        design_temperature:'',
        operating_temperature:'',
        design_life:'',

        cml_number:'',
        cml_description:'',
        actual_outside_diameter_cml:'',
        design_thickness:'',
        structural_thickness:'',
        required_thickness:'',

    }
  },
  mounted() {
    this.fetchData();
    this.pipesize();
  },
  methods: {
    btn1(item){
        this.$router.push({
            path: '/PCL/detail',
            query: { value: item.keyId }
        }) 
      },
    pipesize(){
        const db = this.$fireModule.database();
        db.ref("PIPESIZE").on("value", (snapshot) => {
            const childDate = snapshot.val();
            const items = [];
            for (const keyId in childDate) {
                const datasize = childDate[keyId]; 
                items.push(datasize.pipe_size);
            }
            this.items = items;
        });
    },

    fetchData() {
        const db = this.$fireModule.database();
        db.ref("INFO").on("value", (snapshot) => {
            const childDate = snapshot.val();
            const items = [];
            for (const keyId in childDate) {
                const datauser = childDate[keyId];
                    const item = {
                        keyId,
                        design_life: datauser.design_life || "-",
                        line_number: datauser.line_number || "-",
                        location: datauser.location || "-",
                        from: datauser.from || "-",
                        to: datauser.to || "-",
                        drawing_number: datauser.drawing_number || "-",
                        service: datauser.service || "-",
                        material:datauser.material || "-",
                        inservice_date: datauser.inservice_date || "-",
                        pipe_size: datauser.pipe_size || "-",
                        original_thickness: datauser.original_thickness || "-",
                        stress: datauser.stress || "-",
                        joint_efficiency: datauser.joint_efficiency || "-",
                        ca: datauser.ca || "-",
                        design_pressure: datauser.design_pressure || "-",
                        operating_pressure: datauser.operating_pressure || "-",
                        design_temperature: datauser.design_temperature || "-",
                        operating_temperature: datauser.operating_temperature || "-",
                        Actual_outside: datauser.Actual_outside || "-",
                    };
                items.push(item);
            }
            this.desserts = items;
        });
    },

    SaveData() {
        if(this.line_number === ''){
            alert('กรุณาระบุข้อมูล');
            return;
        }
      try {
        const key = new Date().getTime();
        const db = this.$fireModule.database();
        db.ref("INFO/" + key).set({
          line_number: this.line_number,
          location: this.location,
          from: this.from,
          to: this.to,
          drawing_number: this.drawing_number,
          service: this.service,
          material: this.material,
          inservice_date: this.inservice_date,
          pipe_size: this.pipe_size,
          original_thickness: this.original_thickness,
          stress: this.stress,
          joint_efficiency: this.joint_efficiency,
          ca: this.ca,
          design_pressure: this.design_pressure,
          operating_pressure: this.operating_pressure,
          design_temperature: this.design_temperature,
          operating_temperature: this.operating_temperature,
          design_life : this.design_life,
        });
        db.ref("PIPESIZE").on("value", (snapshot) => {
            const childDate = snapshot.val();
            for (const keyId in childDate) {
                const datasize = childDate[keyId]; 
                if(this.pipe_size === datasize.pipe_size){
                    db.ref("INFO/"+key).update({
                        Actual_outside: datasize.Actual_outside,
                    })
                }
            }
        });
        alert("บันทึกสำเร็จ");
            this.dialogIAdd = false
      }catch (err) {
            // eslint-disable-next-line no-console
            console.log(err);
      }
    },

    Deletedata(senditem){
        const db = this.$fireModule.database();
        db.ref(`INFO/${senditem.keyId}`).remove();
        db.ref(`CML/${senditem.keyId}`).remove();
        db.ref(`TEST_POINT/${senditem.keyId}`).remove();
        db.ref(`THICKNESS/${senditem.keyId}`).remove();
    },

    Saveeditdata(senditem){
        try {
        const db = this.$fireModule.database();
        db.ref(`INFO/${senditem.keyId}`).update({
          design_life: this.design_life,
          line_number: this.line_number,
          location: this.location,
          from: this.from,
          to: this.to,
          drawing_number: this.drawing_number,
          service: this.service,
          material: this.material,
          inservice_date: this.inservice_date,
          pipe_size: this.pipe_size,
          original_thickness: this.original_thickness,
          stress: this.stress,
          joint_efficiency: this.joint_efficiency,
          ca: this.ca,
          design_pressure: this.design_pressure,
          operating_pressure: this.operating_pressure,
          design_temperature: this.design_temperature,
          operating_temperature: this.operating_temperature,
        });
        db.ref("PIPESIZE").on("value", (snapshot) => {
            const childDate = snapshot.val();
            for (const keyId in childDate) {
                const datasize = childDate[keyId]; 
                if(this.pipe_size === datasize.pipe_size){
                    db.ref(`INFO/${senditem.keyId}`).update({
                        Actual_outside: datasize.Actual_outside,
                    })
                }
            }
        });
      }catch (err) {
            // eslint-disable-next-line no-console
            console.log(err);
      }
    },

    Senddatapup(item){
        this.line_number = item.line_number
        this.location = item.location
        this.from = item.from
        this.to = item.to
        this.drawing_number = item.drawing_number
        this.service = item.service
        this.material = item.material
        this.inservice_date = item.inservice_date
        this.pipe_size = item.pipe_size
        this.original_thickness = item.original_thickness
        this.stress = item.stress
        this.joint_efficiency = item.joint_efficiency
        this.ca = item.ca
        this.design_pressure = item.design_pressure
        this.operating_pressure = item.operating_pressure
        this.design_temperature = item.design_temperature
        this.operating_temperature = item.operating_temperature
        this.design_life = item.design_life
    },

    cleardatapup(){
        this.line_number = '';
        this.location = '';
        this.from = '';
        this.to = '';
        this.drawing_number = '';
        this.service = '';
        this.material = '';
        this.inservice_date = '';
        this.pipe_size = '';
        this.original_thickness = '';
        this.stress = '';
        this.joint_efficiency = '';
        this.ca = '';
        this.design_pressure = '';
        this.operating_pressure = '';
        this.design_temperature = '';
        this.operating_temperature = '';
        this.design_life = '';
    },
    clearpipesize(){
        this.pipe_sizeadd = '';
        this.Actual_outside_diameter='';
    },

    addpipesize(){
        if(this.pipe_sizeadd === ''|| this.Actual_outside_diameter===''){
            alert('บันทึกไม่สำเร็จ');
            return;
        }
        const key = new Date().getTime();
        const db = this.$fireModule.database();
        db.ref(`PIPESIZE/${key}`).update({
            pipe_size : this.pipe_sizeadd,
            Actual_outside : this.Actual_outside_diameter,
        })  
        alert('บันทึกสำเร็จ');
    },

    delpipsize(){
        const db = this.$fireModule.database();
        db.ref("PIPESIZE").on("value", (snapshot) => {
            const childDate = snapshot.val();
            const items = [];
            for (const keyId in childDate) {
                const datasize = childDate[keyId]; 
                if(datasize.pipe_size === this.pipe_sizeadd){
                    db.ref(`PIPESIZE/${keyId}`).remove();
                    alert('ลบสำเร็จ');
                }
            }
            this.items = items;
        });
        this.pipesize();
    },

    detailsum(item){
        // eslint-disable-next-line no-console
        console.log(item);
        const db = this.$fireModule.database();
        db.ref("CML/"+item.keyId).on("value", (snapshot) => {
            const childDate = snapshot.val();
            const items = [];
            for (const keyId in childDate) {
                const datauser = childDate[keyId];
                    const item = {
                        keyId,
                        cml_number: datauser.cml_number || "-",
                        cml_description: datauser.cml_description || "-",
                        actual_outside_diameter: datauser.actual_outside_diameter || "-",
                        design_thickness: datauser.design_thickness || "-",
                        structural_thickness: datauser.structural_thickness || "-",
                        required_thickness: datauser.required_thickness || "-",
                    };
                items.push(item);
            }
            this.dessertsdetail = items;
        });
    },
  }
}
</script>