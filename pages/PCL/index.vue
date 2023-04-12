<!-- eslint-disable eqeqeq -->
<!-- eslint-disable eqeqeq -->
<template>
    <div class="container mt-5">
        <div class="blue-grey lighten-3 text-left">
            <h3>PIPING</h3>
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
                @click="dialogIAdd = true"
            ><span>Add Piping</span>
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
                            <span>Info</span>
                            </v-btn>

                            <v-btn
                            color="primary"
                            x-small
                            @click="
                                selectedItem = item;
                                dialogD = true;
                            ">
                            <span>Detail</span>
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
                            <v-text-field
                                v-model="pipe_size"
                                label="Pipe size"
                            ></v-text-field>
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
                            ></v-text-field>
                            <v-text-field
                                label="From"
                                :value = "selectedItem.from"
                            ></v-text-field>
                            <v-text-field
                                label="Drawing number"
                                :value = "selectedItem.drawing_number"
                            ></v-text-field>
                            <v-text-field
                                label="Material"
                                :value = "selectedItem.material"
                            ></v-text-field>
                            <v-text-field
                                label="Pipe size"
                                :value = "selectedItem.pipe_size"
                            ></v-text-field>
                            <v-text-field
                                label="Stress"
                                :value = "selectedItem.stress"
                            ></v-text-field>
                            <v-text-field
                                label="ca"
                                :value = "selectedItem.ca"
                            ></v-text-field>
                            <v-text-field
                                label="design pressure"
                                :value = "selectedItem.design_pressure"
                            ></v-text-field>
                            <v-text-field
                                label="design temperature"
                                :value = "selectedItem.design_temperature"
                            ></v-text-field> -->
                        </v-col>

                        <v-col
                            cols="12"
                            sm="6"
                            >
                            <!-- <v-text-field
                                label="Location"
                                :value = "selectedItem.location"
                            ></v-text-field> 
                            <v-text-field
                                label="To"
                                :value = "selectedItem.to"
                            ></v-text-field>
                            <v-text-field
                                label="Service"
                                :value = "selectedItem.service"
                            ></v-text-field>
                            <v-text-field
                                label="Inservice date"
                                :value = "selectedItem.inservice_date"
                            ></v-text-field>
                            <v-text-field
                                label="Original thickness"
                                :value = "selectedItem.original_thickness"
                            ></v-text-field>
                            <v-text-field
                                label="Joint effciency"
                                :value = "selectedItem.joint_efficiency"
                            ></v-text-field>
                            <v-text-field
                                label="design life"
                                :value = "selectedItem.design_life"
                            ></v-text-field>
                            <v-text-field
                                label="operating pressure"
                                :value = "selectedItem.operating_pressure"
                            ></v-text-field>
                            <v-text-field
                                label="operating temperature"
                                :value = "selectedItem.operating_temperature"
                            ></v-text-field> -->
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
                    Save
                </v-btn>
                <v-btn
                    color="red"
                    text
                    @click="(dialogdel = true)"
                >
                    Delete
                </v-btn>
                <v-btn
                    color="Dark"
                    text
                    @click="dialogI = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup Detail -->
        <div class="text-center">
            <v-dialog
            v-model="dialogD"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                PIPING                             
                </v-card-title>
                
                <v-card-text>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
                </v-card-text>

                <v-divider></v-divider>

                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="primary"
                    text
                    @click="dialogD = false"
                >
                    I accept
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
                            <v-text-field
                                v-model="pipe_size"
                                label="Pipe size"
                            ></v-text-field>
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
                    @click="dialogIAdd = false ,SaveData()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="red"
                    text
                    @click="dialogIAdd = false"
                >
                    Close
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
                    Delete
                </v-btn>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogdel = false"
                >
                    Close
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
                    Save
                </v-btn>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogsave = false"
                >
                    Close
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
        dialogIAdd : false,
        dialogD : false,
        dialogdel : false,
        dialogsave : false,
        desserts: [],

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

    }
  },
  mounted() {
    this.fetchData();
  },
  methods: {
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
                    };
                items.push(item);
            }
            this.desserts = items;
        });
    },

    SaveData() {
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
        });

        alert("บันทึกสำเร็จ");
            console.log("success");
      }catch (err) {
            console.log(err);
      }
    },

    Deletedata(senditem){
        console.log(senditem);
        const db = this.$fireModule.database();
        db.ref(`INFO/${senditem.keyId}`).remove();
    },

    Saveeditdata(senditem){
        console.log(senditem);
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
      }catch (err) {
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
  }
}
</script>