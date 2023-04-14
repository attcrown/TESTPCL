<template>
    <div>
        <div class="container mt-5">
            <div class="blue-grey lighten-3 text-left">
                <h3 class="ms-3 pt-3 pb-3">PIPING</h3>
            </div>
            <v-card
            class="ps-10 pe-10 pt-5 pb-10"
            outlined
            tile
            >
            <h3>LINE NUMBER: {{ info.line_number }}</h3>
            <div>
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <v-card-title class="text-h8">CML</v-card-title>
                    <v-btn elevation="2" color="text-h8 dark lighten-2 pa-2" @click="(dialogAddcml = true),CMLclear(),CMLSUM()"><span>Add CML</span></v-btn>
                </div>
                <v-simple-table
                    fixed-header
                    height="600px"
                >                    
                    <thead>
                        <tr>
                        <th class="text-left">
                            CML number
                        </th>
                        <th class="text-left">
                            CML description
                        </th>
                        <th class="text-left">
                            Actual outside diameter
                        </th>
                        <th class="text-left">
                            Design thickness(mm)
                        </th>
                        <th class="text-left">
                            Structural thickness(mm)
                        </th>
                        <th class="text-left">
                            Required thickness(mm)
                        </th>
                        <th></th>
                        </tr>
                    </thead>
                    <tbody class="">
                        <tr
                        v-for="(itemcml,index) in dessertsdetail" :key="index">
                        <td>{{ itemcml.cml_number}}</td>
                        <td>{{ itemcml.cml_description }}</td>
                        <td>{{ itemcml.actual_outside_diameter }}</td>
                        <td>{{ itemcml.design_thickness }}</td>
                        <td>{{ itemcml.structural_thickness }}</td>
                        <td>{{ itemcml.required_thickness }}</td>
                        <td>
                            <v-btn
                            color="primary"
                            x-small
                            @click="
                                selectedItem = itemcml;
                                editcml(itemcml);
                                dataTP();
                                dialogtestpoint = true;
                            ">
                            <span>View TP</span>
                            </v-btn>
                            <v-btn
                            color="primary"
                            x-small
                            @click="                                
                                dialogeditcml = true;
                                editcml(itemcml);
                            ">
                            <span>Edit</span>
                            </v-btn>
                            <v-btn
                            color="red"
                            x-small
                            @click="
                                selectedItem = itemcml;
                                Deletedata(itemcml);                        
                            ">
                            <span>Delete</span>
                            </v-btn>
                        </td>
                        </tr>
                    </tbody>                
                </v-simple-table>   
            </div>
            </v-card>
        </div>

        <!-- Popup TEST POINT -->
        <v-row justify="center">
            <v-dialog
            v-model="dialogtestpoint"
            persistent
            max-width="800"
            >
            <v-card>
                <v-card-title>
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <v-card-title class="text-h8">TEST POINT</v-card-title>
                        <v-btn elevation="2" color="text-h8 dark lighten-2 pa-2" @click="(dialogAddTP = true),TPclear()"><span>Add TP</span></v-btn>
                    </div>
                </v-card-title>
                    <v-card-text>
                        <v-simple-table
                        fixed-header
                        height="300px"
                    >                    
                        <thead>
                            <tr>
                            <th class="text-left">
                                TP number
                            </th>
                            <th class="text-left">
                                TP description
                            </th>
                            <th class="text-left">
                                Note
                            </th>
                            <th></th>
                            </tr>
                        </thead>
                        <tbody class="">
                            <tr
                            v-for="(itemtp,index) in dessertsTP" :key="index">
                            <td>{{ itemtp.tp_number}}</td>
                            <td>{{ itemtp.tp_description }}</td>
                            <td>{{ itemtp.note_tp }}</td>
                            <td>
                                <v-btn
                                color="primary"
                                x-small
                                @click="
                                    selectedItem = itemtp;
                                    edittp(selectedItem);
                                    dataThickness();
                                    dialogthickness = true;
                                ">
                                <span>View Thickness</span>
                                </v-btn>
                                <v-btn
                                color="primary"
                                x-small
                                @click="  
                                    selectedItem = itemtp;  
                                    edittp(selectedItem);
                                    dialogedittestpoint = true;

                                ">
                                <span>Edit</span>
                                </v-btn>
                                <v-btn
                                color="red"
                                x-small
                                @click="
                                    selectedItem = itemtp;  
                                    edittp(selectedItem);
                                    DeleteTestpoint();
                                ">
                                <span>Delete</span>
                                </v-btn>
                            </td>
                            </tr>
                        </tbody>                
                    </v-simple-table> 
                </v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogtestpoint = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-row>        

        <!-- Popup Thickness -->
        <v-row justify="center">
            <v-dialog
            v-model="dialogthickness"
            persistent
            max-width="700"
            >
            <v-card>
                <v-card-title>
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <v-card-title class="text-h8">THICKNESS</v-card-title>
                        <v-btn elevation="2" color="text-h8 dark lighten-2 pa-2" @click="(dialogaddthickness = true),Thickclear()"><span>Add Thickness</span></v-btn>
                    </div>
                    </v-card-title>
                        <v-card-text>
                            <v-simple-table
                        fixed-header
                        height="300px"
                    >                    
                        <thead>
                            <tr>
                            <th class="text-left">
                                Inspection date
                            </th>
                            <th class="text-left">
                                Actual thickness
                            </th>
                            <th></th>
                            </tr>
                        </thead>
                        <tbody class="">
                            <tr
                            v-for="(itemth,index) in dessertsthickness" :key="index">
                            <td>{{ itemth.Inspection_date}}</td>
                            <td>{{ itemth.Actual_thickness }}</td>
                            <td>
                                <v-btn
                                color="primary"
                                x-small
                                @click=" 
                                    selectedItem = itemth;  
                                    editthink(selectedItem);                               
                                    dialogeditthickness = true;
                                ">
                                <span>Edit</span>
                                </v-btn>
                                <v-btn
                                color="red"
                                x-small
                                @click="
                                    edittp(selectedItem);
                                    DeleteThick();
                                ">
                                <span>Delete</span>
                                </v-btn>
                            </td>
                            </tr>
                        </tbody>                
                    </v-simple-table>
                </v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="dark darken-1"
                    text
                    @click="dialogthickness = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-row>

        <!-- Popup dialogAddcml -->
        <div class="text-center">
            <v-dialog
            v-model="dialogAddcml"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                ADD CML
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
                                v-model="cml_number"
                                label="CML number"
                            ></v-text-field>
                            <v-text-field
                                v-model="cml_description"
                                label="CML description"
                            ></v-text-field>
                            <v-text-field
                                :value="actual_outside_diameter_cml"
                                label="Actual outside diameter"
                            ></v-text-field>
                        </v-col>

                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="design_thickness"
                                label="Design thickness(mm)"
                            ></v-text-field>
                            <v-text-field
                                v-model="structural_thickness"
                                label="Structural thickness(mm)"
                            ></v-text-field>
                            <v-text-field
                                v-model="required_thickness"
                                label="Required thickness(mm)"
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
                    @click="dialogAddcml = false,ADDCMLSUM()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogAddcml = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup dialogeditcml -->
        <div class="text-center">
            <v-dialog
            v-model="dialogeditcml"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                Edit CML
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
                                v-model="cml_number"
                                label="CML number"
                            ></v-text-field>
                            <v-text-field
                                v-model="cml_description"
                                label="CML description"
                            ></v-text-field>
                            <v-text-field
                                :value="actual_outside_diameter_cml"
                                label="Actual outside diameter"
                            ></v-text-field>
                        </v-col>

                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="design_thickness"
                                label="Design thickness(mm)"
                            ></v-text-field>
                            <v-text-field
                                v-model="structural_thickness"
                                label="Structural thickness(mm)"
                            ></v-text-field>
                            <v-text-field
                                v-model="required_thickness"
                                label="Required thickness(mm)"
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
                    @click="dialogeditcml = false,saveeditcml()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogeditcml = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup Edittestpoint -->
        <div class="text-center">
            <v-dialog
            v-model="dialogedittestpoint"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                Edit TP
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
                                v-model="tp_number"
                                label="TP number"
                            ></v-text-field>                            
                        </v-col>
                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="tp_description"
                                label="TP description"
                            ></v-text-field>                            
                        </v-col>
                        <v-col
                        cols="12"
                        sm="12"
                        >
                            <v-text-field
                                    v-model="note_tp"
                                    label="Note"
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
                    @click="saveeditTP(),dialogedittestpoint = false"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogedittestpoint = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup editthickness -->
        <div class="text-center">
            <v-dialog
            v-model="dialogeditthickness"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                Edit Thickness
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
                                v-model="Inspection_date"
                                label="Inspection date"
                            ></v-text-field>                          
                        </v-col>
                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="Actual_thickness"
                                label="Actual thickness"
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
                    @click="dialogeditthickness = false ,saveeditthink()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogeditthickness = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup addthickness -->
        <div class="text-center">
            <v-dialog
            v-model="dialogaddthickness"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                Add Thickness
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
                                v-model="Inspection_date"
                                label="Inspection date"
                            ></v-text-field>                          
                        </v-col>
                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="Actual_thickness"
                                label="Actual thickness"
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
                    @click="dialogaddthickness = false,saveaddthickness()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogaddthickness = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <!-- Popup dialogaddTP -->
        <div class="text-center">
            <v-dialog
            v-model="dialogAddTP"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                ADD TP
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
                                v-model="tp_number"
                                label="TP number"
                            ></v-text-field>                            
                        </v-col>
                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="tp_description"
                                label="TP description"
                            ></v-text-field>                            
                        </v-col>
                        <v-col
                        cols="12"
                        sm="12"
                        >
                            <v-text-field
                                    v-model="note_tp"
                                    label="Note"
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
                    @click="dialogAddTP = false,saveaddtp()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogAddTP = false"
                >
                    Close
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </div>

        <div class="text-center">
            <v-dialog
            v-model="dialogAddcml"
            width="500"
            >
            <v-card>
                <v-card-title class="text-h5 grey lighten-2">
                ADD CML
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
                                v-model="cml_number"
                                label="CML number"
                            ></v-text-field>
                            <v-text-field
                                v-model="cml_description"
                                label="CML description"
                            ></v-text-field>
                            <v-text-field
                                :value="actual_outside_diameter_cml"
                                label="Actual outside diameter"
                            ></v-text-field>
                        </v-col>

                        <v-col
                        cols="12"
                        sm="6"
                        >
                            <v-text-field
                                v-model="design_thickness"
                                label="Design thickness(mm)"
                            ></v-text-field>
                            <v-text-field
                                v-model="structural_thickness"
                                label="Structural thickness(mm)"
                            ></v-text-field>
                            <v-text-field
                                v-model="required_thickness"
                                label="Required thickness(mm)"
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
                    @click="dialogAddcml = false,ADDCMLSUM()"
                >
                    Save
                </v-btn>
                <v-btn
                    color="dark"
                    text
                    @click="dialogAddcml = false"
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
        return{
            id : '',
            dialogAddcml : false,
            dialogI : false,
            dialogAddTP : false,
            dialogtestpoint : false,
            dialogedittestpoint : false,
            dialogthickness : false,
            dialogeditthickness : false,
            dialogeditcml : false,
            dialogaddthickness : false,
            dessertsdetail: [],
            dessertspoint: [],
            dessertsthickness: [],
            dessertsTP: [],
            info : [],

            keyIdcmd: '',
            cml_number:'',
            cml_description:'',
            actual_outside_diameter_cml:'',
            design_thickness:'',
            structural_thickness:'',
            required_thickness:'',

            keyIdtp: '',
            tp_number:'',
            tp_description:'',
            note_tp:'',

            keyIdthick: '',
            Inspection_date:'',
            Actual_thickness:'',

        }
    },  
    mounted() {
        const value = this.$route.query.value;
        this.id = value;
        this.detailsum();
        this.datainfo();
    },
    methods: {
        CMLSUM(){
            this.actual_outside_diameter_cml = this.info.Actual_outside;
            if(this.info.pipe_size <= 2){
                this.structural_thickness = 1.8;
            }else if(this.info.pipe_size === 3){
                this.structural_thickness = 2;
            }else if(this.info.pipe_size === 4){
                this.structural_thickness = 2.3;
            }else if(this.info.pipe_size >= 6 && this.info.pipe_size <= 18){
                this.structural_thickness = 2.8;
            }else if(this.info.pipe_size >= 20){
                this.structural_thickness = 3.1;
            }else{this.structural_thickness = '-'};

            this.design_thickness = (this.info.design_pressure * this.info.Actual_outside)/((2*this.info.stress*this.info.joint_efficiency)+(2 * this.info.design_pressure * 0.4));
            this.required_thickness =  Math.max(this.design_thickness,this.structural_thickness);
        },
        CMLclear(){
            this.cml_number = '';
            this.cml_description = '';
            this.actual_outside_diameter_cml = '';
            this.design_thickness = '';
            this.structural_thickness = '';
            this.required_thickness = '';
        },
        TPclear(){
            this.tp_number = '';
            this.tp_description = '';
            this.note_tp = '';
        },
        Thickclear(){
            this.Inspection_date = '';
            this.Actual_thickness = '';
        },
        detailsum(){
            // eslint-disable-next-line no-console
            const db = this.$fireModule.database();
            db.ref("CML/"+this.id).on("value", (snapshot) => {
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

        editcml(item){
            // eslint-disable-next-line no-console
            const db = this.$fireModule.database();
            db.ref("CML/"+this.id+"/"+item.keyId).on("value", (snapshot) => {
                const childDate = snapshot.val();
                this.keyIdcmd = item.keyId;
                this.cml_number = childDate.cml_number;
                this.cml_description = childDate.cml_description;
                this.actual_outside_diameter_cml = childDate.actual_outside_diameter;
                this.design_thickness = childDate.design_thickness;
                this.structural_thickness = childDate.structural_thickness;
                this.required_thickness = childDate.required_thickness;
            });
        },

        saveeditcml(){
            const db = this.$fireModule.database();
            db.ref(`CML/${this.id}/${this.keyIdcmd}`).update({
                cml_number: this.cml_number,
                cml_description: this.cml_description,
                actual_outside_diameter_cml: this.actual_outside_diameter_cml,
                design_thickness: this.design_thickness,
                structural_thickness: this.structural_thickness,
                required_thickness: this.required_thickness,
            });
        },

        saveaddtp(){
            const key = new Date().getTime();
            const db = this.$fireModule.database();
            db.ref(`TEST_POINT/${this.id}/${this.keyIdcmd}/${key}`).set({
                tp_number: this.tp_number,
                tp_description: this.tp_description,
                note_tp: this.note_tp,
            });
        },

        dataTP(){
            // eslint-disable-next-line no-console
            const db = this.$fireModule.database();
            db.ref(`TEST_POINT/${this.id}/${this.keyIdcmd}/`).on("value", (snapshot) => {
                const childDate = snapshot.val();
                const items = [];
                for (const keyId in childDate) {
                    const datauser = childDate[keyId];
                        const item = {
                            keyId,
                            tp_number: datauser.tp_number || "-",
                            tp_description: datauser.tp_description || "-",
                            note_tp: datauser.note_tp || "-",
                        };
                    items.push(item);
                }
                this.dessertsTP = items;
            });
        },

        edittp(item){
            // eslint-disable-next-line no-console
            const db = this.$fireModule.database();
            db.ref("TEST_POINT/"+this.id+"/"+this.keyIdcmd+"/"+item.keyId).on("value", (snapshot) => {
                const childDate = snapshot.val();
                this.keyIdtp = item.keyId;
                this.tp_number = childDate.tp_number;
                this.tp_description = childDate.tp_description;
                this.note_tp = childDate.note_tp;
            });
        },

        saveeditTP(){
            const db = this.$fireModule.database();
            db.ref("TEST_POINT/"+this.id+"/"+this.keyIdcmd+"/"+this.keyIdtp).update({
                tp_number: this.tp_number,
                tp_description: this.tp_description,
                note_tp: this.note_tp,
            }) 
            alert('บันทึกสำเร็จ');
        },

        datainfo(){
            const db = this.$fireModule.database();
            db.ref("INFO/" + this.id).on("value", (snapshot) => {
                const childDate = snapshot.val();
                const item = {
                    keyId : this.id,
                    design_life: childDate.design_life || "-",
                    line_number: childDate.line_number || "-",
                    location: childDate.location || "-",
                    from: childDate.from || "-",
                    to: childDate.to || "-",
                    drawing_number: childDate.drawing_number || "-",
                    service: childDate.service || "-",
                    material: childDate.material || "-",
                    inservice_date: childDate.inservice_date || "-",
                    pipe_size: childDate.pipe_size || "-",
                    original_thickness: childDate.original_thickness || "-",
                    stress: childDate.stress || "-",
                    joint_efficiency: childDate.joint_efficiency || "-",
                    ca: childDate.ca || "-",
                    design_pressure: childDate.design_pressure || "-",
                    operating_pressure: childDate.operating_pressure || "-",
                    design_temperature: childDate.design_temperature || "-",
                    operating_temperature: childDate.operating_temperature || "-",
                    Actual_outside: childDate.Actual_outside || "-",
                };
                this.info = item;
            });
        },

        Deletedata(senditem){
        const db = this.$fireModule.database();
        db.ref(`CML/${this.id}/${senditem.keyId}`).remove();
        db.ref(`TEST_POINT/${this.id}/${senditem.keyId}/`).remove();
        db.ref(`THICKNESS/${this.id}/${senditem.keyId}/`).remove();
        alert('ลบสำเร็จ');
        },

        ADDCMLSUM(){
            const key = new Date().getTime();
            const db = this.$fireModule.database();
            db.ref(`CML/${this.id}/${key}`).set({
                actual_outside_diameter : this.actual_outside_diameter_cml,
                structural_thickness : this.structural_thickness,
                design_thickness : this.design_thickness,
                required_thickness : this.required_thickness,
                cml_number : this.cml_number,
                cml_description : this.cml_description,
            }) 
            alert('บันทึกสำเร็จ'); 
            window.location.reload();
        },

        saveaddthickness(){
            const key = new Date().getTime();
            const db = this.$fireModule.database();
            db.ref(`THICKNESS/${this.id}/${this.keyIdcmd}/${this.keyIdtp}/${key}`).set({
                Inspection_date : this.Inspection_date,
                Actual_thickness : this.Actual_thickness,
            }) 
            alert('บันทึกสำเร็จ');
        },

        dataThickness(){
            // eslint-disable-next-line no-console
            const db = this.$fireModule.database();
            db.ref(`THICKNESS/${this.id}/${this.keyIdcmd}/${this.keyIdtp}/`).on("value", (snapshot) => {
                const childDate = snapshot.val();
                const items = [];
                for (const keyId in childDate) {
                    const datauser = childDate[keyId];
                        const item = {
                            keyId,
                            Inspection_date: datauser.Inspection_date || "-",
                            Actual_thickness: datauser.Actual_thickness || "-",
                        };
                    items.push(item);
                }
                this.dessertsthickness = items;
            });
        },

        editthink(item){
            this.keyIdthick = item.keyId;
            this.Inspection_date = item.Inspection_date;
            this.Actual_thickness = item.Actual_thickness;
        },

        saveeditthink(){
            const db = this.$fireModule.database();
            db.ref(`THICKNESS/${this.id}/${this.keyIdcmd}/${this.keyIdtp}/${this.keyIdthick}/`).update({
                Inspection_date : this.Inspection_date,
                Actual_thickness : this.Actual_thickness,
            }) 
            alert('บันทึกสำเร็จ');
        },

        DeleteThick(){
            const db = this.$fireModule.database();
            db.ref(`THICKNESS/${this.id}/${this.keyIdcmd}/${this.keyIdtp}/${this.keyIdthick}`).remove();
            alert('ลบสำเร็จ');
        },

        DeleteTestpoint(){
            const db = this.$fireModule.database();
            db.ref(`TEST_POINT/${this.id}/${this.keyIdcmd}/${this.keyIdtp}`).remove();
            db.ref(`THICKNESS/${this.id}/${this.keyIdcmd}/${this.keyIdtp}`).remove();
            alert('ลบสำเร็จ');
        },


    },
}
</script>