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
                        v-for="item in desserts"
                        :key="item.name"
                        >
                        <td class="">{{ item.name }}</td>
                        <td>{{ item.calories }}</td>
                        <td>{{ item.calories }}</td>
                        <td>{{ item.calories }}</td>
                        <td>{{ item.calories }}</td>
                        <td>{{ item.calories }}</td>
                        <td>{{ item.calories }}</td>
                        <td>
                            <v-btn
                            color="primary"
                            x-small
                            @click="
                                selectedItem = item;
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
                                :value = "selectedItem ? selectedItem.name : '-'"
                                label="Line number"
                            ></v-text-field>
                            <v-text-field
                                label="From"

                            ></v-text-field>
                            <v-text-field
                                label="Drawing number"

                            ></v-text-field>
                            <v-text-field
                                label="Material"

                            ></v-text-field>
                            <v-text-field
                                label="Pipe size"

                            ></v-text-field>
                            <v-text-field
                                label="Stress"

                            ></v-text-field>
                            <v-text-field
                                label="ca"

                            ></v-text-field>
                            <v-text-field
                                label="design pressure"

                            ></v-text-field>
                            <v-text-field
                                label="design temperature"

                            ></v-text-field>
                        </v-col>

                        <v-col
                            cols="12"
                            sm="6"
                            >
                            <v-text-field
                                label="Location"
                                
                            ></v-text-field> 
                            <v-text-field
                                label="To"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Service"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Inservice date"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Original thickness"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Joint effciency"
                                
                            ></v-text-field>
                            <v-text-field
                                label="design life"
                                
                            ></v-text-field>
                            <v-text-field
                                label="operating pressure"
                                
                            ></v-text-field>
                            <v-text-field
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
                    @click="dialogI = false"
                >
                    Save
                </v-btn>
                <v-btn
                    color="red"
                    text
                    @click="dialogI = false"
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
                                v-model = line_number
                                label="Line number"
                            ></v-text-field>
                            <v-text-field
                                v-model = from
                                label="From"
                            ></v-text-field>
                            <v-text-field
                                label="Drawing number"
                                v-model = drawing_number
                            ></v-text-field>
                            <v-text-field
                                label="Material"

                            ></v-text-field>
                            <v-text-field
                                label="Pipe size"

                            ></v-text-field>
                            <v-text-field
                                label="Stress"

                            ></v-text-field>
                            <v-text-field
                                label="ca"

                            ></v-text-field>
                            <v-text-field
                                label="design pressure"

                            ></v-text-field>
                            <v-text-field
                                label="design temperature"

                            ></v-text-field>
                        </v-col>

                        <v-col
                            cols="12"
                            sm="6"
                            >
                            <v-text-field
                                label="Location"
                                
                            ></v-text-field> 
                            <v-text-field
                                label="To"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Service"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Inservice date"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Original thickness"
                                
                            ></v-text-field>
                            <v-text-field
                                label="Joint effciency"
                                
                            ></v-text-field>
                            <v-text-field
                                label="design life"
                                
                            ></v-text-field>
                            <v-text-field
                                label="operating pressure"
                                
                            ></v-text-field>
                            <v-text-field
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
                    color="Dark"
                    text
                    @click="dialogIAdd = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

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

        line_number: "",
        location: "",
        from: "",
        to: "",
        drawing_number: "",
        service: "",
        material:"",
        inservice_date:"",
        pipe_size:"",
        original_thickness:"",
        stress:"",
        joint_efficiency:"",
        ca:"",
        design_pressure:"",
        operating_pressure:"",
        design_temperature:"",
        operating_temperature:"",

        desserts: [
          {
            name: 'Frozen Yogurt',
            calories: 159,
          },
          {
            name: 'Ice cream sandwich',
            calories: 237,
          },
        ]
    }
  },
  mounted() {
    // this.fetchData();
  },
  methods: {
    SaveData() {
      try {
        // if (
        //   this.dateclick == "" ||
        //   this.firstname == "" ||
        //   this.selectedBarber == "" ||
        //   this.phonenumber == "" ||
        //   this.selectedTime == ""
        // ) {
        //   alert("บันทึกไม่สำเร็จ");
        //   return;
        // }
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

        // db.ref(`Table/${this.selectedBarber}/${this.dateclick}/${this.selectedTime}`).set({
        //   perple: this.firstname,
        //   phoneNumber: this.phonenumber,
        //   cash:"ไม่มีเงินโอน เนื่องจากช่างเพิ่มคิวด้วยตนเอง",
        // });

        alert("บันทึกสำเร็จ");
        console.log("success");
      } catch (err) {
        console.log(err);
      }
    },
  }
}
</script>